---
title: 'Como: Gravar mensagens de log (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 4b4210983aa5bd57f1b0a89f2f06f089e98670f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594945"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Como: Gravar mensagens de log (Visual Basic)
É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log informações sobre seu aplicativo. Este exemplo mostra como usar o método `My.Application.Log.WriteEntry` para registrar em log informações de rastreamento.  
  
 Para registrar informações de exceção em log, use o método `My.Application.Log.WriteException`; confira [Como: Registrar exceções em log](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o método `My.Application.Log.WriteEntry` para gravar as informações de rastreamento.  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Certifique-se de que os dados gravados no log não incluem informações confidenciais como senhas de usuário. Para obter mais informações, consulte [Working with Application Logs (Trabalhando com logs de aplicativo)](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Como: registrar exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Passo a passo: alterando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
