---
title: Publicar um aplicativo Olá, Mundo com o Visual Studio 2017
description: A publicação cria o conjunto de arquivos necessários para executar seu aplicativo.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.openlocfilehash: 11421c8820dd562ba1dbb5900ba1e9bf944b45d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212125"
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a>Publicar um aplicativo Olá, Mundo com o Visual Studio 2017

Em [Build a C# Hello World Application with .NET Core in Visual Studio 2017](with-visual-studio.md) (Compilar um aplicativo Olá, Mundo em C# com o .NET Core no Visual Studio 2017) ou [Build a Visual Basic Hello World Application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md) (Compilar um aplicativo Olá, Mundo em Visual Basic com o .NET Core no Visual Studio 2017), você compilou um aplicativo de console Olá, Mundo. Em [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) (Depurar um aplicativo Olá, Mundo em C# com o Visual Studio 2017), você o testou usando o depurador do Visual Studio. Agora que você tem certeza de que ele funciona conforme o esperado, publique-o para que outros usuários possam executá-lo. A publicação cria o conjunto de arquivos necessários para executar seu aplicativo e você pode implantá-los copiando-os para um computador de destino.

Para publicar e executar seu aplicativo: 

1. Certifique-se de que o Visual Studio esteja compilando a versão de lançamento de seu aplicativo. Se necessário, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.

   ![Barra de ferramentas do Visual Studio](media/publishing-with-visual-studio/toolbar.png)

1. Clique com o botão direito do mouse no projeto **HelloWorld** (e não na solução HelloWorld) e selecione **Publicar** no menu. Também é possível selecionar **Publicar Hello World** no menu principal **Compilação** do Visual Studio.

   ![Barra de ferramentas do Visual Studio](media/publishing-with-visual-studio/publish1.png)


   ![Barra de ferramentas do Visual Studio](media/publishing-with-visual-studio/publishwindow.png)

1. Abra uma janela de console. Por exemplo, na caixa de texto **Digite aqui para pesquisar** na barra de tarefas do Windows, insira `Command Prompt` (ou apenas `cmd`) e abra uma janela do console selecionando o aplicativo da área de trabalho **Prompt de Comando** ou pressionando Enter se ele estiver selecionado nos resultados da pesquisa.

1. Navegue até o aplicativo publicado no subdiretório `bin\release\PublishOutput` do diretório de projeto do aplicativo. Como mostra a figura a seguir, a saída publicada inclui os seguintes quatro arquivos:

      * *HelloWorld.deps.json*

         Arquivo de dependências de tempo de execução do aplicativo. Define os componentes e as bibliotecas do .NET Core (incluindo a biblioteca de vínculo dinâmico que contém o aplicativo) necessários para executar o aplicativo. Para obter mais informações, consulte [Arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         O arquivo que contém o aplicativo. É uma biblioteca de vínculo dinâmico que pode ser executada inserindo o comando `dotnet HelloWorld.dll` na janela do console. 

      * *HelloWorld.pdb* (opcional para implantação)

         Um arquivo que contém os símbolos de depuração. Não é necessário implantar esse arquivo juntamente com seu aplicativo, embora você deva salvá-lo caso precise depurar a versão publicada do seu aplicativo.

      * *HelloWorld.runtimeconfig.json*

         Arquivo de configuração de tempo de execução do aplicativo. Identifica a versão do .NET Core com base na qual o aplicativo foi criado para ser executado. Para obter mais informações, consulte [Arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Janela de console mostrando arquivos publicados](media/publishing-with-visual-studio/publishedfiles.png)

O processo de publicação cria uma implantação dependente da estrutura, que é um tipo de implantação em que o aplicativo publicado será executado em qualquer plataforma com suporte pelo .NET Core com o .NET Core instalado no sistema. Os usuários podem executar o aplicativo emitindo o comando `dotnet HelloWorld.dll` de uma janela de console.

Para saber mais sobre a publicação e implantação de aplicativos .NET Core, consulte [Implantação de aplicativos .NET Core](../../core/deploying/index.md).
