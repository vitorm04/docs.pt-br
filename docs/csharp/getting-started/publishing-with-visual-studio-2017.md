---
title: Publicar um aplicativo Hello World com o Visual Studio 2017
description: Publicar um aplicativo Hello World com o Visual Studio 2017
keywords: ".NET, .NET core, aplicativo de console .NET Core, publicação (.NET Core), implantação (.NET Core)"
author: stevehoag
ms.author: shoag
ms.date: 10/24/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f4a30d19e111d395088e38c4543c9dacee6105fd
ms.lasthandoff: 03/13/2017

---

# <a name="publishing-your-hello-world-application-with-visual-studio-2017"></a>Publicar um aplicativo Hello World com o Visual Studio 2017

Em [Compilar um aplicativo Hello World em C# com o .NET Core no Visual Studio 2017](with-visual-studio-2017.md), você compilou seu aplicativo de console Hello World, e em [Depurar seu aplicativo Hello World em C# com o Visual Studio 2017](debugging-with-visual-studio-2017.md), você testou usando o depurador do Visual Studio. Agora que você tem certeza de que ele funciona conforme o esperado, publique-o para que outros usuários possam executá-lo. A publicação cria o conjunto de arquivos necessários para executar seu aplicativo; Implante-os copiando-os em um computador de destino.

Para publicar e executar seu aplicativo: 

1. Certifique-se de que o Visual Studio esteja compilando a versão de lançamento de seu aplicativo. Se for necessário, altere a configuração da compilação na barra de ferramentas de **Depurar** para **Versão**, conforme mostra a figura a seguir.

   ![Image](media/release.jpg)

1. Abra uma janela de console. Por exemplo, na caixa de texto **Pergunte-me algo** na barra de tarefas do Windows, digite `Command Prompt` e, em seguida, escolha o aplicativo da área de trabalho **Prompt de Comando** para abrir a janela de console.

1. Clique com o botão direito no projeto Hello World (não na solução Hello World) e selecione **Publicar** no menu. Também é possível selecionar **Publicar Hello World** no menu principal **Compilação** do Visual Studio.

1. Quando a caixa de diálogo **Publicar** mostrada na figura a seguir for exibida, crie um novo perfil de publicação selecionando **Criar novo perfil.**

1. Na caixa de diálogo **Selecionar um destino de publicação** mostrada na figura a seguir, selecione o botão **OK** para publicar seu aplicativo em seu sistema de arquivos local. Ele estará no subdiretório bin\release\PublishOutput do diretório de projeto de seu aplicativo.

1. Agora que você criou um perfil de publicação, selecione o botão **Publicar** na caixa de diálogo **Publicar** mostrada na figura a seguir.

   ![Image](media/publish-2.jpg)

1. Como mostra a figura a seguir, a saída publicada inclui os três arquivos a seguir, que formam seu aplicativo e que podem ser implantados copiando-os em um sistema de destino:

      - HelloWorld.dll
   
      - HelloWorld.deps.json

      - HelloWorld.runtimeconfig.json

   Um quarto arquivo, HelloWorld.pdb, contém os símbolos de depuração. Não é necessário distribuir o arquivo junto com seu aplicativo. No entanto, salve-o caso você precise depurar a versão publicada de seu aplicativo.

   ![Image](media/pub-files.jpg)

O processo de publicação cria uma implantação dependente da estrutura; o aplicativo publicado será executado em qualquer plataforma com suporte no .NET Core, desde que o .NET Core esteja instalado no sistema. Os usuários podem executar o aplicativo emitindo o comando `dotnet.exe HelloWorld.dll` de uma janela de console.

Para saber mais sobre a publicação e implantação de aplicativos .NET Core, consulte [Implantação de aplicativos .NET Core](../../core/deploying/index.md).
