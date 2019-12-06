---
title: Introdução ao .NET Core usando a CLI-CLI do .NET Core
description: Um tutorial passo a passo que mostra como começar a usar o .NET Core no Windows, Linux ou macOS com a CLI (interface de linha de comando) do .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: seodec18,updateeachrelease
ms.openlocfilehash: 4c6a8e495d8532a0ab2e90368663a287731a9af0
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884273"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando

Este artigo mostrará como começar a desenvolver aplicativos de plataformas cruzadas em seu computador usando as ferramentas de CLI do .NET Core.

Se não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/index.md).

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

- [SDK do .NET Core 3,1](https://dotnet.microsoft.com/download) ou versões posteriores.
- Um editor de texto ou de código de sua escolha.

## <a name="hello-console-app"></a>Olá, Aplicativo de Console.

Você pode [exibir ou baixar o código de exemplo](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) do repositório dotnet/samples do GitHub. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Abra um prompt de comando e crie uma pasta chamada *Hello*. Navegue até a pasta que você criou e digite o seguinte:

```dotnetcli
dotnet new console
dotnet run
```

Vejamos um breve passo a passo:

01. `dotnet new console`

    [dotnet novo](../tools/dotnet-new.md) cria um arquivo de projeto *Hello. csproj* atualizado com as dependências necessárias para criar um aplicativo de console. Ele também cria um *Program.cs*, um arquivo básico que contém o ponto de entrada para o aplicativo.
    
    *Olá. csproj*:
    
    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]
    
    O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.
    
    - O elemento `<OutputType>` especifica que estamos criando um executável, em outras palavras, um aplicativo de console.
    - O elemento `<TargetFramework>` especifica qual implementação do .NET Estamos direcionando. Em um cenário avançado, é possível especificar várias estruturas de destino e criar para todas elas em uma única operação. Neste tutorial, iremos criar apenas para o .NET Core 3,1.
    
    *Program.cs*:
    
    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]
    
    O programa é iniciado pelo `using System`, que significa "colocar tudo no namespace `System` no escopo para este arquivo". O namespace `System` inclui a classe `Console`.
    
    Em seguida, definimos um namespace chamado `Hello`. Você pode alterar isso de acordo com a sua vontade. Uma classe chamada `Program` é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres denominada `args`. Essa matriz contém a lista de argumentos passados quando o programa é executado. Como é, essa matriz não é usada e o programa simplesmente grava o texto "Olá, Mundo!" no console. Posteriormente, faremos alterações no código que usará esse argumento.
    
    `dotnet new` chama [dotnet Restore](../tools/dotnet-restore.md) implicitamente. `dotnet restore` chama o [NuGet](https://www.nuget.org/) (gerenciador de pacotes do .NET) para restaurar a árvore de dependências. O NuGet analisa o arquivo *Hello.csproj*, baixa as dependências definidas no arquivo (ou captura-as de um cache no computador) e grava o arquivo *obj/project.assets.json*, que é necessário para compilar e executar a amostra.

02. `dotnet run`

    o [dotnet Run](../tools/dotnet-run.md) chama [dotnet Build](../tools/dotnet-build.md) para garantir que os destinos de compilação tenham sido criados e, em seguida, chama `dotnet <assembly.dll>` para executar o aplicativo de destino.
    
    ```console
    dotnet run

    Hello World!
    ```
    
    Como alternativa, você também pode executar `dotnet build` para compilar o código sem executar os aplicativos de console de compilação. Isso resulta em um aplicativo compilado, como um arquivo DLL, com base no nome do projeto. Nesse caso, o arquivo criado é chamado *Hello. dll*. Esse aplicativo pode ser executado com `dotnet bin\Debug\netcoreapp3.1\Hello.dll` no Windows (use `/` para sistemas não Windows).
    
    ```console
    dotnet bin\Debug\netcoreapp3.1\Hello.dll

    Hello World!
    ```
    
    Quando o aplicativo é compilado, um executável específico do sistema operacional foi criado junto com o `Hello.dll`. No Windows, isso seria `Hello.exe`; no Linux ou no macOS, isso seria `hello`. Com o exemplo acima, o arquivo é nomeado com `Hello.exe` ou `Hello`. Você pode executar esse executável diretamente.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Modificar o programa

Vamos alterar o programa um pouco. Os números de Fibonacci são divertidos, então vamos adicioná-lo e também usar o argumento para saudar a pessoa que está executando o aplicativo.

01. Substitua o conteúdo do arquivo *Program.cs* pelo seguinte código:

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. Execute o [Build dotnet](../tools/dotnet-build.md) para compilar as alterações.

03. Execute o programa passando um parâmetro para o aplicativo. Ao usar o comando `dotnet` para executar um aplicativo, adicione `--` ao final. Qualquer coisa à direita de `--` será passada como um parâmetro para o aplicativo. No exemplo a seguir, o valor `John` é passado para o aplicativo.

    ```console
    $ dotnet run -- John
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

E pronto. Você pode modificar o *Program.cs* da maneira que desejar.

## <a name="working-with-multiple-files"></a>Trabalhando com vários arquivos

Arquivos únicos são bons para programas únicos simples, mas se você estiver criando um aplicativo mais complexo, provavelmente terá vários arquivos de código em seu projeto. Vamos nos basear no exemplo de Fibonacci anterior armazenando em cache alguns valores de Fibonacci e adicionar alguns recursos recursivos.

01. Adicione um novo arquivo no diretório *Hello* chamado *FibonacciGenerator.cs* com o seguinte código:

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. Altere o método `Main` no arquivo *Program.cs* para criar uma instância da nova classe e chame seu método como no seguinte exemplo:

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. Execute o [Build dotnet](../tools/dotnet-build.md) para compilar as alterações.

04. Execute o aplicativo executando [dotnet executar](../tools/dotnet-run.md). O seguinte código mostra a saída do programa:

    ```console
    $ dotnet run
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

Quando estiver pronto para distribuir seu aplicativo, use o comando [dotnet Publish](../tools/dotnet-publish.md) para gerar a pasta de _publicação_ no _bin\\Debug\\netcoreapp 3.1\\publish\\_ (use o `/` para sistemas que não sejam Windows). Você pode distribuir o conteúdo da pasta _publicar_ para outras plataformas, desde que já tenha instalado o runtime dotnet.

```console
dotnet publish
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

A saída acima pode diferir com base na pasta atual e no sistema operacional, mas a saída deve ser semelhante.

Você pode executar o aplicativo publicado com o comando [dotnet](../tools/dotnet.md):

```console
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll

Hello World!
```

Conforme mencionado no início deste artigo, um executável específico do sistema operacional foi criado junto com o `Hello.dll`. No Windows, isso seria `Hello.exe`; no Linux ou no macOS, isso seria `hello`. Com o exemplo acima, o arquivo é nomeado com `Hello.exe` ou `Hello`. Você pode executar esse executável publicado diretamente.

```console
.\bin\Debug\netcoreapp3.1\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Conclusão

E pronto. Agora, é possível começar a usar os conceitos básicos aprendidos aqui para criar seus próprios programas.

## <a name="see-also"></a>Consulte também

- [Organizando e testando projetos com as ferramentas da CLI do .NET Core](testing-with-cli.md)
- [Publicar aplicativos .NET Core com a CLI](../deploying/deploy-with-cli.md)
- [Saiba mais sobre a implantação do aplicativo](../deploying/index.md)
