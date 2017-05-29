---
title: "Implantação de aplicativos .NET Core com o Visual Studio | Microsoft Docs"
description: "Aprenda a implantação de aplicativos .NET Core com o Visual Studio"
keywords: "Implantação do .NET e .NET Core"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 01049a21-fd50-4419-9ab2-0e4a2e091050
ms.translationtype: Human Translation
ms.sourcegitcommit: 3ffe3909902659a22cb25bac6dc5aaa4f5b9fde2
ms.openlocfilehash: c6fe1813f0d09207c6730fc5dce682647e25eb03
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---

# <a name="deploying-net-core-apps-with-visual-studio"></a>Implantando aplicativos .NET Core com o Visual Studio

Você pode implantar um aplicativo .NET Core como uma *implantação dependente de estrutura*, que inclui os binários do seu aplicativo, mas depende da presença do .NET Core no sistema de destino, ou como uma *implantação autocontida*, que inclui os binários do seu aplicativo e do .NET Core. Para obter uma visão geral da implantação de aplicativos .NET Core, consulte [Implantação de aplicativos .NET Core](index.md).

As seções a seguir mostram como usar o Microsoft Visual Studio para criar os seguintes tipos de implantações:

- Implantação dependente de estrutura
- Implantação dependente de estrutura com dependências de terceiros
- Implantação autocontida
- Implantação autocontida com dependências de terceiros

Para obter informações sobre como usar o Visual Studio para desenvolver aplicativos .NET Core, consulte [Pré-requisitos para .NET Core no Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).

## <a name="framework-dependent-deployment"></a>Implantação dependente de estrutura

Implantar uma implantação dependente de estrutura sem dependências de terceiros significa simplesmente compilar, testar e publicar o aplicativo. Um exemplo simples criado em C# ilustra o processo.  

1. Crie o projeto.

   Selecione **Arquivo** > **Novo** > **Projeto**. Na caixa de diálogo **Novo Projeto**, selecione **.NET Core** no painel de tipos de projeto **Instalados** e selecione o modelo **Aplicativo de Console (.NET Core)** no painel central. Insira um nome de projeto, como "FDD" na caixa de texto **Nome**. Selecione o botão **OK**.

1. Adicione o código-fonte do aplicativo.

   Abra o arquivo *Program.cs* no editor e substitua o código gerado automaticamente pelo código a seguir. Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário. Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.

   [!code-cs[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Crie um build de depuração do seu aplicativo.

   Selecione **Compilar** > **Compilar Solução**. Você também pode compilar e executar o build de Depuração do aplicativo selecionando **Depurar** > **Iniciar Depuração**.

1. Implante seu aplicativo.

   Depois de ter depurado e testado o programa, crie os arquivos a serem implantados com seu aplicativo. Para publicar do Visual Studio, faça o seguinte:

      1. Altere a configuração da solução de **Depuração** para **Lançamento** na barra de ferramentas para compilar uma versão de lançamento (em vez de uma de depuração) do aplicativo.

      1. Clique com o botão direito do mouse no projeto (e não na solução) no **Gerenciador de Soluções** e selecione **Publicar**.

      1. Na guia **Publicar**, selecione **Publicar**. O Visual Studio grava os arquivos que compõem seu aplicativo no sistema de arquivos local.

      1. A guia **Publicar** agora mostra um único perfil **FolderProfile**. As configurações do perfil são mostradas na seção **Resumo** da guia.

   Os arquivos resultantes são colocados em um diretório chamado `PublishOutput` que está em um subdiretório de *.\bin\release* do projeto.

Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo. O arquivo é útil principalmente para exceções de depuração. Você pode optar por não empacotá-lo com os arquivos do aplicativo. No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.

Implante o conjunto completo de arquivos de aplicativo da maneira que desejar. Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha. Uma vez instalado, os usuários podem executar seu aplicativo usando o comando `dotnet` e fornecendo o nome de arquivo de aplicativo, como `dotnet fdd.dll`.

Além dos binários do aplicativo, o instalador deverá também agrupar o instalador da estrutura compartilhada ou procurar por ele como um pré-requisito como parte da instalação do aplicativo.  A instalação da estrutura compartilhada requer acesso de Administrador/raiz, pois se trata de todo o computador.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Implantação dependente de estrutura com dependências de terceiros

Implantar uma implantação dependente de estrutura com uma ou mais dependências de terceiros requer que todas as dependências estejam disponíveis para seu projeto. As etapas adicionais a seguir são necessárias antes de ser possível compilar seu aplicativo:

1. Use o **Gerenciador de Pacotes NuGet** para adicionar uma referência a um pacote NuGet ao projeto e se o pacote ainda não estiver disponível no sistema, instale-o. Para abrir o gerenciador de pacotes, selecione **Ferramentas** > **Gerenciador de Pacotes NuGet** > **Gerenciar Pacotes NuGet para a Solução**.

1. Confirme se `Newtonsoft.Json` está instalado em seu sistema e, se não estiver, instale-o. A guia **Instalados** lista os pacotes NuGet instalados no sistema. Se `Newtonsoft.Json` não estiver listado, selecione a guia **Procurar** e insira "Newtonsoft.Json" na caixa de pesquisa. Selecione `Newtonsoft.Json` e, no painel direito, selecione seu projeto antes de selecionar **Instalar**.

1. Se `Newtonsoft.Json` já estiver instalado no sistema, adicione-o ao projeto selecionando o projeto no painel direito da guia **Gerenciar Pacotes para a Solução**.

Observe que uma implantação dependente de estrutura com dependências de terceiros tem a mesma portabilidade que suas dependências de terceiros. Por exemplo, se uma biblioteca de terceiros der suporte apenas a macOS, o aplicativo não será portátil para sistemas Windows. Isso acontecerá se a dependência de terceiros em si depender do código nativo. Um bom exemplo disso é o [servidor Kestrel](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), que requer uma dependência nativa no [libuv](https://github.com/libuv/libuv). Quando uma FDD é criada para um aplicativo com esse tipo de dependência de terceiros, a saída publicada contém uma pasta para cada [RID (Identificador de Tempo de Execução)](../rid-catalog.md#what-are-rids) que dá suporte a dependência nativa (e que existe em seu pacote NuGet).

## <a name="simpleSelf"></a> Implantação autocontida sem dependências de terceiros

Implantar uma implantação autocontida sem dependências de terceiros inclui a criação do projeto, a modificação do arquivo *csproj*, a compilação, os testes e a publicação do aplicativo. Um exemplo simples criado em C# ilustra o processo. 

1. Crie o projeto.

   Selecione **Arquivo** > **Novo** > **Projeto**. Na caixa de diálogo **Adicionar Novo Projeto**, selecione **.NET Core** no painel de tipos de projeto **Instalados** e selecione o modelo **Aplicativo de Console (.NET Core)** no painel central. Insira um nome de projeto, como "SCD" na caixa de texto **Nome** e selecione o botão **OK**.

1. Adicione o código-fonte do aplicativo.

   Abra o arquivo *Program.cs* no editor e substitua o código gerado automaticamente pelo código a seguir. Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário. Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.

   [!code-cs[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Defina as plataformas às quais seu aplicativo se destinará.

   1. Clique com o botão direito do mouse no projeto (e não na solução) no **Gerenciador de Soluções** e selecione **Editar SCD.csproj**.

   1. Crie uma marcação `<RuntimeIdentifiers>` na seção `<PropertyGroup>` de seu arquivo *csproj* que define as plataformas de destino do seu aplicativo e especifique o RID (identificador de tempo de execução) de cada plataforma que você selecionar. Observe que você também precisa adicionar um ponto e vírgula para separar os RIDs. Consulte o [Catálogo de Identificador de Tempo de Execução](../rid-catalog.md) para obter uma lista de identificadores de tempo de execução. 

   Por exemplo, o exemplo a seguir indica que o aplicativo é executado em sistemas operacionais Windows 10 de 64 bits e no sistema de operacional OS X Versão 10.11 de 64 bits.

       ```xml
        <PropertyGroup>
          <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
        </PropertyGroup>
       ```
   Observe que o elemento `<RuntimeIdentifiers>` pode entrar em qualquer `<PropertyGroup>` que você tenha em seu arquivo *csproj*. Um arquivo *csproj* de exemplo completo aparece mais adiante nesta seção.

1. Crie um build de depuração do seu aplicativo.

   Selecione **Compilar** > **Compilar Solução**. Você também pode compilar e executar o build de Depuração do aplicativo selecionando **Depurar** > **Iniciar Depuração**.

1. Publique seu aplicativo.

   Depois de ter depurado e testado o programa, crie os arquivos a serem implantados com seu aplicativo para cada plataforma à qual ele se destina.

   Para publicar seu aplicativo do Visual Studio, faça o seguinte:

      1. Altere a configuração da solução de **Depuração** para **Lançamento** na barra de ferramentas para compilar uma versão de lançamento (em vez de uma de depuração) do aplicativo.

      1. Clique com o botão direito do mouse no projeto (e não na solução) no **Gerenciador de Soluções** e selecione **Publicar**. 

      1. Na guia **Publicar**, selecione **Publicar**. O Visual Studio grava os arquivos que compõem seu aplicativo no sistema de arquivos local.

      1. A guia **Publicar** agora mostra um único perfil **FolderProfile**. As configurações do perfil são mostradas na seção **Resumo** da guia. **Tempo de Execução de Destino** identifica qual tempo de execução foi publicado e **Local de Destino** identifica o local em que os arquivos da implantação autocontida foram gravados.

      1. Por padrão, o Visual Studio grava todos os arquivos publicados em um único diretório. Para sua conveniência, é melhor criar perfis separados para cada tempo de execução de destino e colocar os arquivos publicados em um diretório específico da plataforma. Isso envolve a criação de um perfil de publicação separado para cada plataforma de destino. Agora recompile o aplicativo para cada plataforma fazendo o seguinte:

         1. Selecione **Criar novo perfil** na caixa de diálogo **Publicar**.

         1. Na caixa de diálogo **Escolher um destino de publicação**, altere o local de **Escolher uma pasta** para *bin\Release\PublishOutput\win10-x64*. Selecione **OK**.

         1. Selecione o novo perfil (**FolderProfile1**) na lista de perfis e certifique-se de que o **Tempo de Execução de Destino** é `win10-x64`. Se não for, selecione **Configurações**. Na caixa de diálogo **Configurações de Perfil**, altere o **Tempo de Execução de Destino** para `win10-x64` e selecione **Salvar**. Caso contrário, selecione **Cancelar**.

         1. Selecione **Publicar** para publicar seu aplicativo para plataformas Windows 10 de 64 bits.

         1. Siga as etapas anteriores novamente para criar um perfil para a plataforma `osx.10.11-x64`. O **Local de Destino** é *bin\Release\PublishOutput\osx.10.11-x64* e o **Tempo de Execução de Destino** é `osx.10.11-x64`. O nome que o Visual Studio atribui a este perfil é **FolderProfile2**.

      Observe que cada local de destino contém o conjunto completo de arquivos (arquivos do seu aplicativo e todos os arquivos do .NET Core) necessários para iniciar seu aplicativo.

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

Implantar uma implantação autocontida com uma ou mais dependências de terceiros envolve adicionar as dependências. As etapas adicionais a seguir são necessárias antes de ser possível compilar seu aplicativo:

1. Use o **Gerenciador de Pacotes NuGet** para adicionar uma referência a um pacote NuGet ao projeto e se o pacote ainda não estiver disponível no sistema, instale-o. Para abrir o gerenciador de pacotes, selecione **Ferramentas** > **Gerenciador de Pacotes NuGet** > **Gerenciar Pacotes NuGet para a Solução**.

1. Confirme se `Newtonsoft.Json` está instalado em seu sistema e, se não estiver, instale-o. A guia **Instalados** lista os pacotes NuGet instalados no sistema. Se `Newtonsoft.Json` não estiver listado, selecione a guia **Procurar** e insira "Newtonsoft.Json" na caixa de pesquisa. Selecione `Newtonsoft.Json` e, no painel direito, selecione seu projeto antes de selecionar **Instalar**.

1. Se `Newtonsoft.Json` já estiver instalado no sistema, adicione-o ao projeto selecionando o projeto no painel direito da guia **Gerenciar Pacotes para a Solução**.

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

Observe que você só pode implantar uma implantação autocontida com uma biblioteca de terceiros para plataformas compatíveis com essa biblioteca. Isso é semelhante a ter dependências de terceiros com dependências nativas em sua implantação dependente de estrutura, em que as dependências nativas não existem na plataforma de destino a menos que elas tenham sido instaladas anteriormente.

# <a name="see-also"></a>Consulte também
[Implantação de aplicativos .NET Core](index.md)   
[Catálogo do Identificador de Tempo de Execução do .NET Core](../rid-catalog.md)   

