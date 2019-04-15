---
title: 'Solução de problemas: Ouvintes de log (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 12282df50bc42d2a153a9aa8db01f2654acd91ce
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299521"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Solução de problemas: Ouvintes de log (Visual Basic)
É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo.  
  
 Para determinar quais ouvintes de log recebem essas mensagens, confira [Passo a passo: Determinando o local em que My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 O objeto `Log` pode usar filtragem de log para limitar a quantidade de informações que ele registra no log. Se os filtros tiverem sido configurados incorretamente, os logs poderão conter informações incorretas. Para obter mais informações sobre a filtragem, confira [Passo a passo: Filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 No entanto, se um log tiver sido configurado incorretamente, talvez seja necessário obter mais informações sobre sua configuração atual. É possível obter essas informações por meio da propriedade `TraceSource` avançada do log.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Para determinar os ouvintes de log do objeto Log no código  
  
1. Importe o namespace <xref:System.Diagnostics> no início do arquivo de código. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Crie uma função que retorna uma cadeia de caracteres que consiste de informações para cada um dos ouvintes de log.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Passe a coleção dos ouvintes de rastreamento do log para a função `GetListeners` e exiba o valor retornado.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Trabalhar com logs do aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Passo a passo: determinar o local no qual My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
