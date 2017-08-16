---
title: Publicar um aplicativo Hello World com o Visual Studio 2017
description: "A publicação cria o conjunto de arquivos necessários para executar seu aplicativo."
keywords: ".NET, .NET Core, aplicativo do console, publicação, implantação"
author: BillWagner
ms.author: wiwagn
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: 1c4fbefb23fc47cf035085f76ec1c10d5422a6f5
ms.contentlocale: pt-br
ms.lasthandoff: 05/03/2017

---

# <a name="publishing-your-hello-world-application-with-visual-studio-2017"></a>Publicar um aplicativo Hello World com o Visual Studio 2017

Em [Compilando um aplicativo Olá, Mundo em C# com o .NET Core no Visual Studio 2017](with-visual-studio.md), você criou um aplicativo de console Olá, Mundo. Em [Depurando um aplicativo Olá, Mundo em C# com o Visual Studio 2017](debugging-with-visual-studio.md), você o testou usando o depurador do Visual Studio. Agora que você tem certeza de que ele funciona conforme o esperado, publique-o para que outros usuários possam executá-lo. A publicação cria o conjunto de arquivos necessários para executar seu aplicativo e você pode implantá-los copiando-os para um computador de destino.

Para publicar e executar seu aplicativo: 

1. Certifique-se de que o Visual Studio esteja compilando a versão de lançamento de seu aplicativo. Se necessário, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.

   ![Barra de ferramentas do Visual Studio](media/publishing-with-visual-studio/toolbar.png)

1. Clique com o botão direito do mouse no projeto **HelloWorld** (e não na solução HelloWorld) e selecione **Publicar** no menu. Também é possível selecionar **Publicar Hello World** no menu principal **Compilação** do Visual Studio.

   ![Barra de ferramentas do Visual Studio](media/publishing-with-visual-studio/publish1.png)

1. Na janela de publicação **HelloWorld**, a pasta de saída de publicação padrão é fornecida na caixa de texto **Escolher uma pasta**. Selecione o botão **Publicar**.

   ![Barra de ferramentas do Visual Studio](media/publishing-with-visual-studio/publishwindow.png)

1. Abra uma janela de console. Por exemplo, na caixa de texto **Pergunte-me alguma coisa** na barra de tarefas do Windows, insira `Command Prompt` (ou `cmd` de forma abreviada) e abra uma janela de console selecionando o aplicativo da área de trabalho **Prompt de Comando** ou pressionando Enter se ele estiver selecionado nos resultados da pesquisa.

1. Navegue até o aplicativo publicado no subdiretório `bin\release\PublishOutput` do diretório de projeto do aplicativo. Como mostra a figura a seguir, a saída publicada inclui os seguintes quatro arquivos:

      * *HelloWorld.deps.json*
      * *HelloWorld.dll*
      * *HelloWorld.pdb* (opcional para implantação)
      * *HelloWorld.runtimeconfig.json*

   O arquivo *HelloWorld.pdb* contém símbolos de depuração. Não é necessário implantar esse arquivo juntamente com seu aplicativo, embora você deva salvá-lo caso precise depurar a versão publicada do seu aplicativo.

   ![Janela de console mostrando arquivos publicados](media/publishing-with-visual-studio/publishedfiles.png)

O processo de publicação cria uma implantação dependente da estrutura, que é um tipo de implantação em que o aplicativo publicado será executado em qualquer plataforma com suporte pelo .NET Core com o .NET Core instalado no sistema. Os usuários podem executar o aplicativo emitindo o comando `dotnet HelloWorld.dll` de uma janela de console.

Para saber mais sobre a publicação e implantação de aplicativos .NET Core, consulte [Implantação de aplicativos .NET Core](../../core/deploying/index.md).

