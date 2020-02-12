---
title: Сборка приложения .NET для Apache Spark в Ubuntu
description: Сведения о том, как скомпилировать приложение .NET для Apache Spark в Ubuntu.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: a12c861d0f231910f715a13fd41d1f3f0d6748a7
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76928070"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a><span data-ttu-id="f8929-103">Сведения о том, как скомпилировать приложение .NET для Apache Spark в Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="f8929-103">Learn how to build your .NET for Apache Spark application on Ubuntu</span></span>

<span data-ttu-id="f8929-104">В этой статье представлены сведения о том, как скомпилировать приложение .NET для Apache Spark в Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="f8929-104">This article teaches you how to build your .NET for Apache Spark applications on Ubuntu.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f8929-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="f8929-105">Prerequisites</span></span>

<span data-ttu-id="f8929-106">Если у вас уже есть все перечисленные ниже компоненты, перейдите к [сборке](#build).</span><span class="sxs-lookup"><span data-stu-id="f8929-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

1. <span data-ttu-id="f8929-107">Скачайте и установите пакет SDK для **[.NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1)** или **[.NET Core 3.1.](https://dotnet.microsoft.com/download/dotnet-core/3.1)** . После этого в путь будет добавлена цепочка инструментов `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="f8929-107">Download and install **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** or the **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - installing the SDK adds the `dotnet` toolchain to your path.</span></span>  <span data-ttu-id="f8929-108">Поддерживается .NET Core версий 2.1, 2.2 и 3.1.</span><span class="sxs-lookup"><span data-stu-id="f8929-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>

2. <span data-ttu-id="f8929-109">Установите **[OpenJDK 8](https://openjdk.java.net/install/)** .</span><span class="sxs-lookup"><span data-stu-id="f8929-109">Install **[OpenJDK 8](https://openjdk.java.net/install/)**.</span></span> 

   - <span data-ttu-id="f8929-110">Вы можете использовать следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f8929-110">You can use the following command:</span></span>

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * <span data-ttu-id="f8929-111">Убедитесь в том, что можно выполнить команду `java` в командной строке.</span><span class="sxs-lookup"><span data-stu-id="f8929-111">Verify you are able to run `java` from your command-line.</span></span>       

      <span data-ttu-id="f8929-112">Пример выходных данных java-version:</span><span class="sxs-lookup"><span data-stu-id="f8929-112">Sample java -version output:</span></span>
          
      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * <span data-ttu-id="f8929-113">Если вы уже установили несколько версий OpenJDK и хотите выбрать OpenJDK 8, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f8929-113">If you already have multiple OpenJDK versions installed and want to select OpenJDK 8, use the following command:</span></span>

      ```bash
      sudo update-alternatives --config java
      ```

3. <span data-ttu-id="f8929-114">Установите **[Apache Maven 3.6.0 или более поздней версии](https://maven.apache.org/download.cgi)** .</span><span class="sxs-lookup"><span data-stu-id="f8929-114">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>

   * <span data-ttu-id="f8929-115">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f8929-115">Run the following command:</span></span>

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```
       
       <span data-ttu-id="f8929-116">Обратите внимание, что при закрытии терминала эти переменные среды не будут сохранены.</span><span class="sxs-lookup"><span data-stu-id="f8929-116">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="f8929-117">Если вы хотите, чтобы изменения были постоянными, добавьте строки `export` в файл `~/.bashrc`.</span><span class="sxs-lookup"><span data-stu-id="f8929-117">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="f8929-118">Убедитесь в том, что можно выполнить команду `mvn` в командной строке.</span><span class="sxs-lookup"><span data-stu-id="f8929-118">Verify you are able to run `mvn` from your command-line</span></span>       

       <span data-ttu-id="f8929-119">Пример выходных данных mvn -version:</span><span class="sxs-lookup"><span data-stu-id="f8929-119">Sample mvn -version output:</span></span>
       
       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. <span data-ttu-id="f8929-120">Установите **[Apache Spark 2.3 или более поздней версии](https://spark.apache.org/downloads.html)** .</span><span class="sxs-lookup"><span data-stu-id="f8929-120">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
<span data-ttu-id="f8929-121">Скачайте [Apache Spark 2.3 или более поздней версии](https://spark.apache.org/downloads.html) и извлеките содержимое в локальную папку (например, `~/bin/spark-2.3.2-bin-hadoop2.7`).</span><span class="sxs-lookup"><span data-stu-id="f8929-121">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7`).</span></span> <span data-ttu-id="f8929-122">Поддерживаются версии Spark 2.3.\*, 2.4.0, 2.4.1, 2.4.3 и 2.4.4.</span><span class="sxs-lookup"><span data-stu-id="f8929-122">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * <span data-ttu-id="f8929-123">Добавьте необходимые [переменные среды](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (например, `~/bin/spark-2.3.2-bin-hadoop2.7/`) и `PATH` (например, `$SPARK_HOME/bin:$PATH`).</span><span class="sxs-lookup"><span data-stu-id="f8929-123">Add the necessary [environment variables](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7/`) and `PATH` (e.g., `$SPARK_HOME/bin:$PATH`)</span></span>

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```
       
      <span data-ttu-id="f8929-124">Обратите внимание, что при закрытии терминала эти переменные среды не будут сохранены.</span><span class="sxs-lookup"><span data-stu-id="f8929-124">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="f8929-125">Если вы хотите, чтобы изменения были постоянными, добавьте строки `export` в файл `~/.bashrc`.</span><span class="sxs-lookup"><span data-stu-id="f8929-125">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="f8929-126">Убедитесь в том, что можно выполнить команду `spark-shell` в командной строке.</span><span class="sxs-lookup"><span data-stu-id="f8929-126">Verify you are able to run `spark-shell` from your command-line.</span></span>

      <span data-ttu-id="f8929-127">Пример выходных данных в консоли.</span><span class="sxs-lookup"><span data-stu-id="f8929-127">Sample console output:</span></span>
      
      ```
      Welcome to
            ____              __
           / __/__  ___ _____/ /__
          _\ \/ _ \/ _ `/ __/  '_/
         /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
            /_/

      Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
      Type in expressions to have them evaluated.
      Type :help for more information.

      scala> sc
      res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
      ```                      

<span data-ttu-id="f8929-128">Перед переходом к следующему разделу еще раз убедитесь, что можно выполнять команды `dotnet`, `java`, `mvn` и `spark-shell` из командной строки.</span><span class="sxs-lookup"><span data-stu-id="f8929-128">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="f8929-129">Считаете, что есть более эффективный способ?</span><span class="sxs-lookup"><span data-stu-id="f8929-129">Feel there is a better way?</span></span> <span data-ttu-id="f8929-130">[Сообщите о проблеме](https://github.com/dotnet/spark/issues) и поделитесь своим мнением.</span><span class="sxs-lookup"><span data-stu-id="f8929-130">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

## <a name="build"></a><span data-ttu-id="f8929-131">Построить</span><span class="sxs-lookup"><span data-stu-id="f8929-131">Build</span></span>

<span data-ttu-id="f8929-132">Для выполнения задач оставшейся части этого руководства потребуется копия репозитория .NET для Apache Spark, клонированная на локальный компьютер, например `~/dotnet.spark/`.</span><span class="sxs-lookup"><span data-stu-id="f8929-132">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine e.g., `~/dotnet.spark/`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a><span data-ttu-id="f8929-133">Сборка уровня расширений Scala в .NET для Spark</span><span class="sxs-lookup"><span data-stu-id="f8929-133">Build .NET for Spark Scala extensions layer</span></span>

<span data-ttu-id="f8929-134">Когда вы отправляете приложение .NET, .NET для Apache Spark применяет соответствующую логику на языке Scala, которая информирует Apache Spark о методах обработки запросов (таких как запрос на создание нового сеанса Spark, запрос на передачу данных от .NET на виртуальную машину Java и т. п.).</span><span class="sxs-lookup"><span data-stu-id="f8929-134">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="f8929-135">Эту логику можно найти в [исходном коде Scala в .NET для Apache Spark](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="f8929-135">This logic can be found in the [.NET for Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="f8929-136">Следующий шаг: сборка уровня расширений Scala в .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f8929-136">The next step is to build the .NET for Apache Spark Scala extension layer:</span></span>

```bash
cd src/scala
mvn clean package 
```

<span data-ttu-id="f8929-137">Здесь должны быть JAR-файлы, созданные для поддерживаемых версий Spark:</span><span class="sxs-lookup"><span data-stu-id="f8929-137">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a><span data-ttu-id="f8929-138">Сборка примеров приложений .NET с помощью .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="f8929-138">Build .NET sample applications using .NET Core CLI</span></span>

<span data-ttu-id="f8929-139">В этом разделе объясняется, как создать [примеры приложений](https://github.com/dotnet/spark/tree/master/examples) для .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="f8929-139">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="f8929-140">Эти шаги помогут составить представление об общем процессе сборки для любого приложения .NET для Spark.</span><span class="sxs-lookup"><span data-stu-id="f8929-140">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

1. <span data-ttu-id="f8929-141">Скомпилируйте рабочую роль:</span><span class="sxs-lookup"><span data-stu-id="f8929-141">Build the worker:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```
      
   <span data-ttu-id="f8929-142">Пример выходных данных в консоли.</span><span class="sxs-lookup"><span data-stu-id="f8929-142">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
      
      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```

2. <span data-ttu-id="f8929-143">Скомпилируйте примеры:</span><span class="sxs-lookup"><span data-stu-id="f8929-143">Build the samples:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```
      
   <span data-ttu-id="f8929-144">Пример выходных данных в консоли.</span><span class="sxs-lookup"><span data-stu-id="f8929-144">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="f8929-145">Запуск примеров приложений .NET для Spark</span><span class="sxs-lookup"><span data-stu-id="f8929-145">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="f8929-146">После сборки примеров вы можете отправить приложения .NET Core с помощью `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="f8929-146">Once you build the samples, you can use `spark-submit` to submit your .NET Core apps.</span></span> <span data-ttu-id="f8929-147">Убедитесь, что выполнены все [предварительные требования](#prerequisites) и установка Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="f8929-147">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

1. <span data-ttu-id="f8929-148">Включите в переменную среды `DOTNET_WORKER_DIR` или `PATH` путь, по которому был создан двоичный файл `Microsoft.Spark.Worker` (например, `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span><span class="sxs-lookup"><span data-stu-id="f8929-148">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. <span data-ttu-id="f8929-149">Откройте терминал и перейдите к каталогу, где был создан двоичный файл приложения (например, `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span><span class="sxs-lookup"><span data-stu-id="f8929-149">Open a terminal and go to the directory where your app binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. <span data-ttu-id="f8929-150">Приложение запускается по единой общей схеме.</span><span class="sxs-lookup"><span data-stu-id="f8929-150">Running your app follows the basic structure:</span></span>

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   <span data-ttu-id="f8929-151">Вот несколько примеров, которые вы можете выполнить:</span><span class="sxs-lookup"><span data-stu-id="f8929-151">Here are some examples you can run:</span></span>

   * <span data-ttu-id="f8929-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)** .</span><span class="sxs-lookup"><span data-stu-id="f8929-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * <span data-ttu-id="f8929-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)** .</span><span class="sxs-lookup"><span data-stu-id="f8929-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * <span data-ttu-id="f8929-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)** .</span><span class="sxs-lookup"><span data-stu-id="f8929-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * <span data-ttu-id="f8929-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)** .</span><span class="sxs-lookup"><span data-stu-id="f8929-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```