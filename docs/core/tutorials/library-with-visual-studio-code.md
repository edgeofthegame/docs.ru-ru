---
title: Создание библиотеки классов .NET Standard с помощью Visual Studio Code
description: Сведения о создании библиотеки классов .NET Standard с помощью Visual Studio Code.
ms.date: 06/08/2020
ms.openlocfilehash: 966b9b0b48f67809e82d9133c523995cd97b6015
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495516"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a>Учебник. Создание библиотеки .NET Standard с помощью Visual Studio Code

В этом руководстве вы создадите простую служебную библиотеку с одним методом для обработки строк. Вы реализуете его как [метод расширения](../../csharp/programming-guide/classes-and-structs/extension-methods.md), чтобы вызывать его так же, как любой член класса <xref:System.String>.

*Библиотека классов* определяет типы и методы, которые могут быть вызваны из любого приложения. Библиотеку классов, предназначенную для .NET Standard 2.0, можно вызывать из любой реализации .NET, которая поддерживает эту версию .NET Standard. Когда вы завершите создание библиотеки классов, можете распространить ее как независимый компонент или включить в состав одного или нескольких пакетов приложения.

## <a name="prerequisites"></a>Предварительные требования

1. Установленная платформа [Visual Studio Code](https://code.visualstudio.com/) с [расширением C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp). См. сведения об [установке расширений Visual Studio Code из Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [Пакет SDK для .NET Core 3.1 или более поздней версии](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>Создание решения

Начните с создания пустого решения для размещения проекта библиотеки классов. Решение служит контейнером для одного или нескольких проектов. Вы будете добавлять дополнительные связанные проекты в одно решение.

1. Запустите Visual Studio Code.

1. В главном меню выберите **Файл** > **Открыть папку** (в macOS щелкните **Открыть...** ).

1. В диалоговом окне **Открыть папку** создайте папку *ClassLibraryProjects* и щелкните **Выбор папки** (в macOS щелкните **Открыть**).

1. Откройте **терминал** в Visual Studio Code, выбрав в основном меню пункт **Вид** > **Терминал**.

   Откроется окно **Терминал** с командной строкой в папке *ClassLibraryProjects*.

1. В **окне терминала** введите следующую команду:

   ```dotnetcli
   dotnet new sln
   ```

   Выходные данные в терминале выглядят примерно так, как в следующем примере:

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a>Создание проекта библиотеки классов

Добавьте в решение новый проект библиотеки классов .NET Standard с именем "StringLibrary".

1. В терминале выполните следующую команду, чтобы создать проект библиотеки классов:

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   Команда `-o` или `--output` задает расположение для размещения созданных выходных данных.

   Выходные данные в терминале выглядят примерно так, как в следующем примере:

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj (in 328 ms).
   Restore succeeded.
   ```

1. Чтобы добавить проект библиотеки в решение, выполните следующую команду:

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   Выходные данные в терминале выглядят примерно так, как в следующем примере:

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. Проверьте, предназначена ли библиотека для правильной версии .NET Standard. В **обозревателе** откройте файл *StringLibrary/StringLibrary.csproj*.

   Элемент `TargetFramework` показывает, что проект предназначен для .NET Standard 2.0.

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. Откройте файл *Class1.cs* и замените его содержимое следующим кодом:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   Библиотека классов `UtilityLibraries.StringLibrary` содержит метод `StartsWithUpper`, который возвращает значение <xref:System.Boolean>, указывающее, является ли первым символом текущего экземпляра строки символ верхнего регистра. Символы верхнего регистра определяются по стандарту Юникод. Метод <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> возвращает `true`, если символ является символом верхнего регистра.

1. Сохраните файл.

1. Выполните следующую команду, чтобы выполнить сборку решения и убедиться, что проект компилируется без ошибок.

   ```dotnetcli
   dotnet build
   ```

   Выходные данные в терминале выглядят примерно так, как в следующем примере:

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a>Добавление консольного приложения в решение

Добавьте консольное приложение, использующее библиотеку классов. В приложении пользователю будет предложено ввести строку и сообщить, начинается ли строка с символа верхнего регистра.

1. В терминале выполните следующую команду, чтобы создать проект консольного приложения:

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   Выходные данные в терминале выглядят примерно так, как в следующем примере:

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj (in 210 ms).
   Restore succeeded.
   ```

1. Чтобы добавить проект консольного приложения в решение, выполните следующую команду:

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   Выходные данные в терминале выглядят примерно так, как в следующем примере:

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. Откройте файл *ShowCase/Program.cs* и замените все его содержимое следующим кодом:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   В этом коде используется переменная `row` для сохранения количества строк данных, записываемых в окно консоли. Всякий раз, когда оно достигает значения 25 или превышает его, код очищает окно консоли и отображается сообщение для пользователя.

   Сама программа предлагает пользователю ввести строку. Она сообщает, начинается ли строка с символа верхнего регистра. Если пользователь нажимает клавишу <kbd>ВВОД</kbd>, не введя никакой строки, приложение завершает свою работу и окно консоли закрывается.

1. Сохраните изменения.

## <a name="add-a-project-reference"></a>Добавление ссылки на проект

Изначально новый проект консольного приложения не имеет доступа к библиотеке классов. Чтобы позволить приложению вызывать методы из библиотеки классов, создайте в проекте ссылку на проект библиотеки классов.

1. Выполните следующую команду:

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   Выходные данные в терминале выглядят примерно так, как в следующем примере:

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a>Запуск приложения

1. Выполните следующую команду в окне терминала:

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. Проверьте, как работает программа: вводите строки и нажимайте клавишу <kbd>ВВОД</kbd>. Чтобы выйти, нажмите клавишу <kbd>ВВОД</kbd>.

   Выходные данные в терминале выглядят примерно так, как в следующем примере:

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a>Дополнительные ресурсы

* [Разработка библиотек с помощью .NET Core CLI](libraries.md)
* [Список версий .NET Standard и поддерживаемых ими платформ](../../standard/net-standard.md)

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы создали решение, добавили проект библиотеки и добавили проект консольного приложения, использующего библиотеку. В следующем руководстве вы добавите в решение проект модульного теста.

> [!div class="nextstepaction"]
> [Тестирование библиотеки .NET Standard с помощью .NET Core и Visual Studio Code](testing-library-with-visual-studio-code.md)
