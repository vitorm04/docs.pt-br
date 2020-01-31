---
title: Publicar seu aplicativo .NET Core Olá, Mundo com o Visual Studio
description: A publicação cria o conjunto de arquivos necessários para executar seu aplicativo .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: a82934fd2ea9568681a3bec82c3b15513decc926
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741573"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>Publicar seu aplicativo .NET Core Olá, Mundo com o Visual Studio

Em [criar um aplicativo Olá, mundo com o .NET Core no Visual Studio](with-visual-studio.md), você criou um aplicativo de console Olá, mundo. Em [depurar seu aplicativo Olá, mundo com o Visual Studio](debugging-with-visual-studio.md), você o testou usando o depurador do Visual Studio. Agora que você tem certeza de que ele funciona conforme o esperado, publique-o para que outros usuários possam executá-lo. A publicação cria o conjunto de arquivos necessários para executar seu aplicativo. Para implantar os arquivos, copie-os para o computador de destino.

## <a name="publish-the-app"></a>Publique o aplicativo

1. Certifique-se de que o Visual Studio esteja compilando a versão de lançamento de seu aplicativo. Se necessário, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.

   ![Barra de ferramentas do Visual Studio com build de versão selecionado](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Clique com o botão direito do mouse no projeto **HelloWorld** (e não na solução HelloWorld) e selecione **Publicar** no menu. (Você também pode selecionar **publicar HelloWorld** no menu principal do **Build** .)

   ![Menu de contexto Publicar do Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)
   
1. Na página **escolha um destino de publicação** , selecione **pasta**e, em seguida, selecione **Criar perfil**.

   ![Escolher um destino de publicação no Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)
   
1. Na página **publicar** , selecione **publicar**.

   ![Janela Publicar do Visual Studio](media/publishing-with-visual-studio/publish-page.png)
   
## <a name="inspect-the-files"></a>Inspecionar os arquivos

O processo de publicação cria uma implantação dependente de estrutura, que é um tipo de implantação em que o aplicativo publicado é executado em qualquer plataforma com suporte do .NET Core com o .NET Core instalado no sistema. Os usuários podem executar o aplicativo publicado clicando duas vezes no executável ou emitindo o comando `dotnet HelloWorld.dll` em um prompt de comando.

Nas etapas a seguir, você examinará os arquivos criados pelo processo de publicação.

1. Abra um prompt de comando.

   Uma maneira de abrir um prompt de comando é inserir o **prompt de comando** (ou **cmd** por curto) na caixa de pesquisa na barra de tarefas do Windows. Selecione o **prompt de comando** aplicativo da área de trabalho ou pressione **Enter** se ele já estiver selecionado nos resultados da pesquisa.

1. Navegue até o aplicativo publicado no subdiretório *bin\Release\netcoreapp3.1\publish* do diretório do projeto do aplicativo.

   ![Janela de console mostrando arquivos publicados](media/publishing-with-visual-studio/published-files-output.png)

   Como mostra a imagem, a saída publicada inclui os seguintes arquivos:

      * *HelloWorld.deps.json*

         Este é o arquivo de dependências de tempo de execução do aplicativo. Ele define os componentes do .NET Core e as bibliotecas (incluindo a biblioteca de vínculo dinâmico que contém seu aplicativo) necessárias para executar o aplicativo. Para obter mais informações, consulte [arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld.dll*

         Esta é a versão de [implantação dependente de estrutura](../deploying/deploy-with-cli.md#framework-dependent-deployment) do aplicativo. Para executar essa biblioteca de vínculo dinâmico, insira `dotnet HelloWorld.dll` em um prompt de comando.

      * *HelloWorld. exe*
      
         Esta é a versão [executável dependente de estrutura](../deploying/deploy-with-cli.md#framework-dependent-executable) do aplicativo. Para executá-lo, insira `HelloWorld.exe` em um prompt de comando.

      * *HelloWorld.pdb* (opcional para implantação)

         Este é o arquivo de símbolos de depuração. Não é necessário implantar esse arquivo juntamente com seu aplicativo, embora você deva salvá-lo caso precise depurar a versão publicada do seu aplicativo.

      * *HelloWorld.runtimeconfig.json*

         Este é o arquivo de configuração de tempo de execução do aplicativo. Identifica a versão do .NET Core com base na qual o aplicativo foi criado para ser executado. Você também pode adicionar opções de configuração a ela. Para obter mais informações, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="additional-resources"></a>Recursos adicionais

- [Implantação de aplicativos do .NET Core](../deploying/index.md)
