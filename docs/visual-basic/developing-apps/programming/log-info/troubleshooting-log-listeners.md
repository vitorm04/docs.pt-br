---
title: 'Solucionando problemas: ouvintes de Log'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346862"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Solucionando problemas: ouvintes de log (Visual Basic)

É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo.  
  
 Para determinar quais ouvintes de log recebem essas mensagens, consulte [Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 O objeto `Log` pode usar filtragem de log para limitar a quantidade de informações que ele registra no log. Se os filtros tiverem sido configurados incorretamente, os logs poderão conter informações incorretas. Para obter informações sobre filtragem, consulte [Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
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
- [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
