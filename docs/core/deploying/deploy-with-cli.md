---
title: "Implantação de aplicativos .NET Core com as ferramentas da CLI"
description: "Aprenda a implantação de aplicativos .NET Core com ferramentas da CLI (interface de linha de comando)"
keywords: "Implantação do .NET e .NET Core"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 82ebe16d-5e1c-46cc-91e8-71974296429c
ms.workload: dotnetcore
ms.openlocfilehash: 302383ec44afd91d1df7f6c717b268d5f965c8c9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>Implantando aplicativos .NET Core com ferramentas da CLI (interface de linha de comando)

Você pode implantar um aplicativo .NET Core como uma *implantação dependente de estrutura*, que inclui os binários do seu aplicativo, mas depende da presença do .NET Core no sistema de destino, ou como uma *implantação autocontida*, que inclui os binários do seu aplicativo e do .NET Core. Para obter uma visão geral, consulte [Implantação de aplicativos .NET Core](index.md).

As seções a seguir mostram como usar [ferramentas de interface de linha de comando do .NET Core](../tools/index.md) para criar os seguintes tipos de implantações:

- Implantação dependente de estrutura
- Implantação dependente de estrutura com dependências de terceiros
- Implantação autocontida
- Implantação autocontida com dependências de terceiros

Ao trabalhar na linha de comando, você pode usar um editor de programa de sua escolha. Se o editor de programa for o [Visual Studio Code](https://code.visualstudio.com), você poderá abrir um console de comando dentro do ambiente do Visual Studio Code selecionando **Exibir** > **Terminal Integrado**.

## <a name="framework-dependent-deployment"></a>Implantação dependente de estrutura

Implantar uma implantação dependente de estrutura sem dependências de terceiros significa simplesmente compilar, testar e publicar o aplicativo. Um exemplo simples criado em C# ilustra o processo. 

1. Crie um diretório de projeto.

   Crie um diretório para seu projeto e torne-o o diretório atual.

1. Crie o projeto.

   Na linha de comando, digite [dotnet new console](../tools/dotnet-new.md) para criar um novo projeto de console em C# naquele diretório.

1. Adicione o código-fonte do aplicativo.

   Abra o arquivo *Program.cs* no editor e substitua o código gerado automaticamente pelo código a seguir. Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário. Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Atualize as ferramentas e as dependências do projeto.
 
   Execute o comando [dotnet restore](../tools/dotnet-restore.md) ([veja observação](#dotnet-restore-note)) para restaurar as dependências especificadas no projeto.

1. Crie um build de depuração do seu aplicativo.

   Use o comando [dotnet build](../tools/dotnet-build.md) para compilar o aplicativo ou o comando [dotnet run](../tools/dotnet-run.md) para compilá-lo e executá-lo.

1. Implante seu aplicativo.

   Depois de ter depurado e testado o programa, crie a implantação usando o seguinte comando:

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   Isso cria uma versão de Lançamento (em vez de Depuração) de seu aplicativo. Os arquivos resultantes são colocados em um diretório chamado *publish* que está em um subdiretório do diretório *bin* do seu projeto.

Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo. O arquivo é útil principalmente para exceções de depuração. Você pode optar por não distribui-lo com os arquivos do aplicativo. No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.

Você pode implantar o conjunto completo de arquivos de aplicativo da maneira que desejar. Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha. Uma vez instalado, os usuários podem executar seu aplicativo usando o comando `dotnet` e fornecendo o nome de arquivo de aplicativo, como `dotnet fdd.dll`.

Além dos binários do aplicativo, o instalador deverá também agrupar o instalador da estrutura compartilhada ou procurar por ele como um pré-requisito como parte da instalação do aplicativo.  A instalação da estrutura compartilhada requer acesso de Administrador/raiz.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Implantação dependente de estrutura com dependências de terceiros

Implantar uma implantação dependente de estrutura com uma ou mais dependências de terceiros requer que as dependências estejam disponíveis para seu projeto. São necessárias duas etapas adicionais antes de executar o comando `dotnet restore` ([veja observação](#dotnet-restore-note)):

1. Adicione referências para as bibliotecas de terceiros necessárias à seção `<ItemGroup>` do arquivo *csproj*. A seção `<ItemGroup>` a seguir contém uma dependência no [Json.NET](http://www.newtonsoft.com/json) como uma biblioteca de terceiros:

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. Se você ainda não o fez, baixe o pacote NuGet contendo a dependência de terceiros. Para baixar o pacote, execute o comando `dotnet restore` ([veja observação](#dotnet-restore-note)) depois de adicionar a dependência. Como a dependência é resolvida fora do cache local do NuGet no momento da publicação, ela deve estar disponível no seu sistema.

Observe que uma implantação dependente de estrutura com dependências de terceiros tem a mesma portabilidade que suas dependências de terceiros. Por exemplo, se uma biblioteca de terceiros der suporte apenas a macOS, o aplicativo não será portátil para sistemas Windows. Isso acontecerá se a dependência de terceiros em si depender do código nativo. Um bom exemplo disso é o [servidor Kestrel](/aspnet/core/fundamentals/servers/kestrel), que requer uma dependência nativa no [libuv](https://github.com/libuv/libuv). Quando uma FDD é criada para um aplicativo com esse tipo de dependência de terceiros, a saída publicada contém uma pasta para cada [RID (Identificador de Tempo de Execução)](../rid-catalog.md) que dá suporte a dependência nativa (e que existe em seu pacote NuGet).

## <a name="simpleSelf"></a> Implantação autocontida sem dependências de terceiros

Implantar uma implantação autocontida sem dependências de terceiros inclui a criação do projeto, a modificação do arquivo *csproj*, a compilação, os testes e a publicação do aplicativo. Um exemplo simples criado em C# ilustra o processo. O exemplo mostra como criar uma implantação autocontida usando o [utilitário dotnet](../tools/dotnet.md) da linha de comando.

1. Crie um diretório para o projeto.

   Crie um diretório para seu projeto e torne-o o diretório atual.

1. Crie o projeto.

   Na linha de comando, digite [dotnet new console](../tools/dotnet-new.md) para criar um novo projeto de console em C# naquele diretório.

1. Adicione o código-fonte do aplicativo.

   Abra o arquivo *Program.cs* no editor e substitua o código gerado automaticamente pelo código a seguir. Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário. Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Defina as plataformas às quais seu aplicativo se destinará.

   Crie uma marcação `<RuntimeIdentifiers>` na seção `<PropertyGroup>` de seu arquivo *csproj* que define as plataformas de destino do seu aplicativo e especifique o RID (identificador de tempo de execução) de cada plataforma que você selecionar. Observe que você também precisa adicionar um ponto e vírgula para separar os RIDs. Consulte o [Catálogo de Identificador de Tempo de Execução](../rid-catalog.md) para obter uma lista de identificadores de tempo de execução. 

   Por exemplo, a seção `<PropertyGroup>` a seguir indica que o aplicativo é executado em sistemas operacionais Windows 10 de 64 bits e no sistema de operacional OS X Versão 10.11 de 64 bits.

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   Observe que o elemento `<RuntimeIdentifiers>` pode aparecer em qualquer `<PropertyGroup>` em seu arquivo *csproj*. Um arquivo *csproj* de exemplo completo aparece mais adiante nesta seção.

1. Atualize as ferramentas e as dependências do projeto.

   Execute o comando [dotnet restore](../tools/dotnet-restore.md) ([veja observação](#dotnet-restore-note)) para restaurar as dependências especificadas no projeto.

1. Crie um build de depuração do seu aplicativo.

   Na linha de comando, use o comando [dotnet build](../tools/dotnet-build.md).

1. Depois de ter depurado e testado o programa, crie os arquivos a serem implantados com seu aplicativo para cada plataforma à qual ele se destina.

   Use o comando `dotnet publish` para as duas plataformas de destino da seguinte maneira:

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   Isso cria uma versão de Lançamento (em vez de Depuração) do seu aplicativo para cada plataforma de destino. Os arquivos resultantes são colocados em um subdiretório chamado *publish* que está em um subdiretório de *.\bin\Release\netcoreapp1.1\<runtime_identifier>* do seu projeto. Observe que cada subdiretório contém o conjunto completo de arquivos (arquivos do seu aplicativo e todos os arquivos do .NET Core) necessários para iniciar seu aplicativo.

Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo. O arquivo é útil principalmente para exceções de depuração. Você pode optar por não empacotá-lo com os arquivos do aplicativo. No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.

Implante os arquivos publicados na maneira que desejar. Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha.

A seguir está o arquivo *csproj* completo para esse projeto.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Implantação autocontida com dependências de terceiros

Implantar uma implantação autocontida com uma ou mais dependências de terceiros envolve adicionar as dependências. São necessárias duas etapas adicionais antes de executar o comando `dotnet restore` ([veja observação](#dotnet-restore-note)):

1. Adicione referências a quaisquer bibliotecas de terceiros à seção `<ItemGroup>` de seu arquivo *csproj*. A seção `<ItemGroup>` a seguir usa Json.NET como uma biblioteca de terceiros.

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. Se você ainda não o fez, baixe o pacote NuGet que contém a dependência de terceiros para seu sistema. Para disponibilizar a dependência para seu aplicativo, execute o comando `dotnet restore` ([veja observação](#dotnet-restore-note)) depois de adicionar a dependência. Como a dependência é resolvida fora do cache local do NuGet no momento da publicação, ela deve estar disponível no seu sistema.

A seguir está o arquivo *csproj* completo para esse projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

Quando você implanta seu aplicativo, todas as dependências de terceiros usadas em seu aplicativo também contém os arquivos do aplicativo. As bibliotecas de terceiros não são necessárias no sistema em que o aplicativo está em execução.

Observe que você só pode implantar uma implantação autocontida com uma biblioteca de terceiros para plataformas compatíveis com essa biblioteca. Isso é semelhante a ter dependências de terceiros com dependências nativas em uma implantação dependente de estrutura, em que as dependências nativas devem ser compatíveis com a plataforma para a qual o aplicativo é implantado.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a>Consulte também

[Implantação de aplicativos .NET Core](index.md)   
[Catálogo do Identificador de Tempo de Execução do .NET Core](../rid-catalog.md)   

