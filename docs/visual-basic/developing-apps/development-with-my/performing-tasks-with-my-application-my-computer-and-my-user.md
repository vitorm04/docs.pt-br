---
title: Executando tarefas com My. Application, My. Computer e My. User (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Application object, developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object, developing applications
- My.User object, developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: 7
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2a51579ae571385ce0ccfa6b45593de818dcf1bc
ms.lasthandoff: 03/13/2017

---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Executando tarefas com My.Application, My.Computer e My.User (Visual Basic)
Os três centrais `My` são objetos que fornecem acesso às informações e comumente usado funcionalmente `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), e `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</xref:Microsoft.VisualBasic.ApplicationServices.User> </xref:Microsoft.VisualBasic.Devices.Computer> </xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> Você pode usar esses objetos para acessar informações relacionadas para o aplicativo atual, que o aplicativo é instalado no computador ou o usuário atual do aplicativo, respectivamente.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My. Application, My. Computer e My. User  
 Os exemplos a seguir demonstram como informações podem ser recuperadas usando `My`.  
  
 [!code-vb[VbVbcnMy n º&1;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy n º&2;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 Além de recuperar informações, os membros expostos através desses três objetos também permitem que sejam executados métodos relacionados a esse objeto. Por exemplo, você pode acessar uma variedade de métodos para manipular arquivos ou atualizar o registro através de `My.Computer`.  
  
 E/s de arquivos é significativamente mais fácil e rápida com `My`, que inclui uma variedade de métodos e propriedades para manipular arquivos, pastas e unidades. O <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>objeto permite que você ler grandes estruturas de arquivos que têm delimitador ou largura fixa de campos.</xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Este exemplo abre o `TextFieldParser``reader` e o usa para ler de `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser&#23;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 `My.Application`permite alterar a cultura do seu aplicativo. O exemplo a seguir demonstra como esse método pode ser chamado.  
  
 [!code-vb[VbVbcnMy n º&3;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
