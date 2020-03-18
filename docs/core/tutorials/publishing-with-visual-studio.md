---
title: Publique seu aplicativo .NET Core Hello World com o Visual Studio
description: A publicação cria o conjunto de arquivos necessários para executar seu aplicativo .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156628"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>Publique seu aplicativo .NET Core Hello World com o Visual Studio

Em [Criar um aplicativo Hello World com .NET Core no Visual Studio,](with-visual-studio.md)você construiu um aplicativo de console Hello World. Em [Depurar seu aplicativo Hello World com o Visual Studio,](debugging-with-visual-studio.md)você o testou usando o depurador visual studio. Agora que você tem certeza de que ele funciona conforme o esperado, publique-o para que outros usuários possam executá-lo. A publicação cria o conjunto de arquivos necessários para executar seu aplicativo. Para implantar os arquivos, copie-os para a máquina de destino.

## <a name="publish-the-app"></a>Publicar o aplicativo

1. Certifique-se de que o Visual Studio esteja compilando a versão de lançamento de seu aplicativo. Se necessário, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.

   ![Barra de ferramentas do Visual Studio com build de versão selecionado](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Clique com o botão direito do mouse no projeto **HelloWorld** (não na solução HelloWorld) e **selecione Publicar** no menu. (Você também pode selecionar **Publicar HelloWorld** no menu principal **da Build.)**

   ![Menu de contexto Publicar do Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. Na **escolha de uma página-alvo de publicação,** selecione **Pasta**e selecione **Criar perfil**.

   ![Escolha um alvo de publicação no Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. Na página **Publicar,** **selecione Publicar**.

   ![Janela Publicar do Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>Inspecione os arquivos

O processo de publicação cria uma implantação dependente da estrutura, que é um tipo de implantação onde o aplicativo publicado é executado em qualquer plataforma suportada pelo .NET Core com .NET Core instalado no sistema. Os usuários podem executar o aplicativo publicado clicando duas `dotnet HelloWorld.dll` vezes no executável ou emitindo o comando a partir de um prompt de comando.

Nas etapas seguintes, você verá os arquivos criados pelo processo de publicação.

1. Abra um prompt de comando.

   Uma maneira de abrir um prompt de comando é inserir **o Prompt de comando** (ou **cmd** para abreviar) na caixa de pesquisa na barra de tarefas do Windows. Selecione o aplicativo de desktop **Command Prompt** ou **pressione Enter** se ele já estiver selecionado nos resultados da pesquisa.

1. Navegue até o aplicativo publicado no *bin\Release\netcoreapp3.1\publish* subdiretório do diretório de projeto do aplicativo.

   ![Janela de console mostrando arquivos publicados](media/publishing-with-visual-studio/published-files-output.png)

   Como a imagem mostra, a saída publicada inclui os seguintes arquivos:

      * *HelloWorld.deps.json*

         Este é o arquivo de dependências de tempo de execução do aplicativo. Ele define os componentes do .NET Core e as bibliotecas (incluindo a biblioteca de links dinâmicos que contém seu aplicativo) necessários para executar o aplicativo. Para obter mais informações, consulte [arquivos de configuração do Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld.dll*

         Esta é a versão [de implantação dependente](../deploying/deploy-with-cli.md#framework-dependent-deployment) da estrutura do aplicativo. Para executar esta biblioteca `dotnet HelloWorld.dll` de links dinâmicos, digite em um prompt de comando.

      * *HelloWorld.exe*

         Esta é a versão [executável dependente](../deploying/deploy-with-cli.md#framework-dependent-executable) da estrutura do aplicativo. Para executá-lo, digite `HelloWorld.exe` em um prompt de comando.

      * *HelloWorld.pdb* (opcional para implantação)

         Este é o arquivo de símbolos de depuração. Não é necessário implantar esse arquivo juntamente com seu aplicativo, embora você deva salvá-lo caso precise depurar a versão publicada do seu aplicativo.

      * *HelloWorld.runtimeconfig.json*

         Este é o arquivo de configuração em tempo de execução do aplicativo. Identifica a versão do .NET Core com base na qual o aplicativo foi criado para ser executado. Você também pode adicionar opções de configuração a ele. Para obter mais informações, consulte [as configurações de configuração em tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="additional-resources"></a>Recursos adicionais

- [Implantação de aplicativos .NET Core](../deploying/index.md)
