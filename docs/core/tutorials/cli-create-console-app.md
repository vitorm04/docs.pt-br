---
title: Introdução ao .NET Core, usando as ferramentas da CLI
description: Um tutorial passo-a-passo mostrando como começar com o .NET Core no Windows, Linux ou macOS usando o .NET Core CLI.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240851"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>Comece com o .NET Core usando o .NET Core CLI

Este artigo mostrará como começar a desenvolver aplicativos .NET Core que funcionam no Windows, Linux e macOS usando o .NET Core CLI.

Se você não estiver familiarizado com o .NET Core CLI, consulte a visão geral do [.NET Core CLI](../tools/index.md).

## <a name="prerequisites"></a>Pré-requisitos

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download) ou versões posteriores.
- Um editor de texto ou editor de código de sua escolha.

## <a name="hello-console-app"></a>Olá, Aplicativo de Console.

Você pode [exibir ou baixar o código de exemplo](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) do repositório dotnet/samples do GitHub. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Abra um prompt de comando e crie uma pasta chamada *Hello*. Navegue até a pasta que você criou e digite o seguinte.

```dotnetcli
dotnet new console
dotnet run
```

Vejamos um breve passo a passo:

01. `dotnet new console`

    [dotnet new](../tools/dotnet-new.md) cria um arquivo de projeto *Hello.csproj* atualizado com as dependências necessárias para construir um aplicativo de console. Ele também cria um *Program.cs*, um arquivo básico contendo o ponto de entrada para o aplicativo.

    *Olá.csproj:*

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.

    - O `<OutputType>` elemento especifica que estamos construindo um executável, ou seja, um aplicativo de console.
    - O `<TargetFramework>` elemento especifica qual a implementação .NET que estamos direcionando. Em um cenário avançado, é possível especificar várias estruturas de destino e criar para todas elas em uma única operação. Neste tutorial, vamos continuar a construir apenas para .NET Core 3.1.

    *Program.cs:*

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    O programa é iniciado pelo `using System`, que significa "colocar tudo no namespace `System` no escopo para este arquivo". O `System` namespace inclui `Console` a classe.

    Em seguida, definimos um namespace chamado `Hello`. Você pode alterar isso de acordo com a sua vontade. Uma classe `Program` nomeada é definida dentro `Main` desse namespace, com um `args`método que leva uma matriz de strings nomeada . Esta matriz contém a lista de argumentos aprovados quando o programa é executado. Como é, esta matriz não é usada e o programa simplesmente escreve o texto "Hello World!" no console. Posteriormente, faremos alterações no código que usará esse argumento.

    `dotnet new`chamadas [dotnet restaurar](../tools/dotnet-restore.md) implicitamente. `dotnet restore` chama o [NuGet](https://www.nuget.org/) (gerenciador de pacotes do .NET) para restaurar a árvore de dependências. O NuGet analisa o arquivo *Hello.csproj*, baixa as dependências definidas no arquivo (ou captura-as de um cache no computador) e grava o arquivo *obj/project.assets.json*, que é necessário para compilar e executar a amostra.

02. `dotnet run`

    [dotnet executar](../tools/dotnet-run.md) chamadas [dotnet build](../tools/dotnet-build.md) para garantir que os alvos `dotnet <assembly.dll>` de compilação foram construídos e, em seguida, chamadas para executar o aplicativo de destino.

    ```dotnetcli
    dotnet run
    ```

    Você tem a seguinte saída.

    ```console
    Hello World!
    ```

    Alternativamente, você também `dotnet build` pode executar para compilar o código sem executar os aplicativos de console de compilação. Isso resulta em um aplicativo compilado, como um arquivo DLL, com base no nome do projeto. Neste caso, o arquivo criado é chamado *Hello.dll*. Este aplicativo pode `dotnet bin\Debug\netcoreapp3.1\Hello.dll` ser executado `/` com o Windows (uso para sistemas não-Windows).

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    Você tem a seguinte saída.

    ```console
    Hello World!
    ```

    Quando o aplicativo é compilado, um executável específico do `Hello.dll`sistema operacional foi criado junto com o . No Windows, isso `Hello.exe`seria; no Linux ou macOS, `hello`isso seria . Com o exemplo acima, o `Hello.exe` `Hello`arquivo é nomeado com ou . Você pode executar isso executável diretamente.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Modificar o programa

Vamos alterar o programa um pouco. Os números de Fibonacci são divertidos, então vamos adicionar isso e também usar o argumento para cumprimentar a pessoa que está executando o aplicativo.

01. Substitua o conteúdo do arquivo *Program.cs* pelo seguinte código:

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. Executar [a compilação dotnet](../tools/dotnet-build.md) para compilar as alterações.

03. Execute o programa passando um parâmetro para o aplicativo. Quando você `dotnet` usar o comando para `--` executar um aplicativo, adicione ao final. Qualquer coisa à `--` direita será passada como parâmetro para o aplicativo. No exemplo a seguir, o valor `John` é passado para o aplicativo.

    ```dotnetcli
    dotnet run -- John
    ```

    Você tem a seguinte saída.

    ```console
    Hello John!
    Fibonacci Numbers 1-15:
    1: 0
    2: 1
    3: 1
    4: 2
    5: 3
    6: 5
    7: 8
    8: 13
    9: 21
    10: 34
    11: 55
    12: 89
    13: 144
    14: 233
    15: 377
    ```

E isso é tudo! Você pode modificar *Program.cs* do jeito que quiser.

## <a name="working-with-multiple-files"></a>Trabalhando com vários arquivos

Arquivos únicos são bons para programas pontuais simples, mas se você está construindo um aplicativo mais complexo, você provavelmente terá vários arquivos de código em seu projeto. Vamos nos basear no exemplo de Fibonacci anterior armazenando em cache alguns valores de Fibonacci e adicionar alguns recursos recursivos.

01. Adicione um novo arquivo no diretório *Hello* chamado *FibonacciGenerator.cs* com o seguinte código:

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. Altere o método `Main` no arquivo *Program.cs* para criar uma instância da nova classe e chame seu método como no seguinte exemplo:

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. Executar [a compilação dotnet](../tools/dotnet-build.md) para compilar as alterações.

04. Execute seu aplicativo executando [a execução dotnet run](../tools/dotnet-run.md).

    ```dotnetcli
    dotnet run
    ```

    Você tem a seguinte saída.

    ```console
    0
    1
    1
    2
    3
    5
    8
    13
    21
    34
    55
    89
    144
    233
    377
    ```

## <a name="publish-your-app"></a>Publicar seu aplicativo

Uma vez que você esteja pronto para distribuir seu aplicativo, use o comando [dotnet publish](../tools/dotnet-publish.md) para `/` gerar a pasta de _publicação_ no _\\bin debug\\netcoreapp3.1\\publish\\ _ (uso para sistemas não-Windows). Você pode distribuir o conteúdo da pasta _publicar_ para outras plataformas, desde que já tenha instalado o runtime dotnet.

```dotnetcli
dotnet publish
```

Você tem saída semelhante à seguinte.

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

A saída acima pode diferir com base na pasta atual e no sistema operacional, mas a saída deve ser semelhante.

Você pode executar o aplicativo publicado com o comando [dotnet](../tools/dotnet.md):

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

Você tem a seguinte saída.

```console
Hello World!
```

Como mencionado no início deste artigo, foi criado um executável `Hello.dll`específico do sistema operacional juntamente com o . No Windows, isso `Hello.exe`seria; no Linux ou macOS, `hello`isso seria . Com o exemplo acima, o `Hello.exe` `Hello`arquivo é nomeado com ou . Você pode executar este executável publicado diretamente.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Conclusão

E isso é tudo! Agora, é possível começar a usar os conceitos básicos aprendidos aqui para criar seus próprios programas.

## <a name="see-also"></a>Confira também

- [Organização e teste de projetos com o .NET Core CLI](testing-with-cli.md)
- [Publique os aplicativos .NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md)
- [Implantação de aplicativos .NET Core](../deploying/index.md)
