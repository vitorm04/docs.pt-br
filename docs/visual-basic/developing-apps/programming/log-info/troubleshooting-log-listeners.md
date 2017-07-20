---
title: "Solução de problemas: ouvintes de log (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b651902563a60a68443f7d3f3b917a9c1ae085bc
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Solucionando problemas: ouvintes de log (Visual Basic)
É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo.  
  
 Para determinar quais ouvintes de log recebem essas mensagens, consulte [Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 O objeto `Log` pode usar filtragem de log para limitar a quantidade de informações que ele registra no log. Se os filtros tiverem sido configurados incorretamente, os logs poderão conter informações incorretas. Para obter informações sobre filtragem, consulte [Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 No entanto, se um log tiver sido configurado incorretamente, talvez seja necessário obter mais informações sobre sua configuração atual. É possível obter essas informações por meio da propriedade `TraceSource` avançada do log.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Para determinar os ouvintes de log do objeto Log no código  
  
1.  Importe o namespace <xref:System.Diagnostics> no início do arquivo de código. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  Crie uma função que retorna uma cadeia de caracteres que consiste de informações para cada um dos ouvintes de log.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  Passe a coleção dos ouvintes de rastreamento do log para a função `GetListeners` e exiba o valor retornado.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [Trabalhando com Logs de Aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
