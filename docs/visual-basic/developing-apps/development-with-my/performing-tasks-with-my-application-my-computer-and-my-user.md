---
title: Executando tarefas com My.Application, My.Computer e My.User (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d55e0b3a126f2216d005c7bddbcaefb7d8f0a580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Executando tarefas com My.Application, My.Computer e My.User (Visual Basic)
Os três centrais `My` são objetos que fornecem acesso a informações e comumente usadas funcionalidade `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), e `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Você pode usar esses objetos para acessar informações relacionadas para o aplicativo atual, o que o aplicativo é instalado no computador ou o usuário atual do aplicativo, respectivamente.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My. Application, My. Computer e My. User  
 Os exemplos a seguir demonstram como informações podem ser recuperadas usando `My`.  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 Além de recuperar informações do, os membros expostos através desses três objetos também permitem que você execute métodos relacionados a esse objeto. Por exemplo, você pode acessar uma variedade de métodos para manipular arquivos ou atualizar o registro por meio de `My.Computer`.  
  
 E/s de arquivos é significativamente mais fácil e rápido com `My`, que inclui uma variedade de métodos e propriedades para manipular arquivos, pastas e unidades. O <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> objeto permite que você ler grandes estruturas de arquivos que têm delimitador ou largura fixa de campos. Este exemplo abre o `TextFieldParser``reader` e usa para ler de `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 `My.Application`permite que você alterar a cultura do seu aplicativo. O exemplo a seguir demonstra como esse método pode ser chamado.  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
