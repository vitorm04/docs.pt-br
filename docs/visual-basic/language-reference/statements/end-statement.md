---
title: "Instrução End"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b692409f2895f5e9b713c57fc35ff2def40bce75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="end-statement"></a>Instrução End
Finaliza a execução imediatamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
End  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar o `End` instrução em qualquer lugar em um procedimento para forçar o aplicativo inteiro para interromper a execução. `End`Fecha todos os arquivos abertos com um `Open` instrução e limpa todas as variáveis do aplicativo. O aplicativo fecha assim que existem em outros programas que contenham referências a seus objetos e nenhum dos seu código está em execução.  
  
> [!NOTE]
>  O `End` instrução interrompe a execução de código abruptamente e não chama o `Dispose` ou `Finalize` método ou qualquer outro código do Visual Basic. Referências a objetos mantidas por outros programas são invalidadas. Se um `End` instrução for encontrada dentro de um `Try` ou `Catch` bloco, o controle passará para o correspondente `Finally` bloco.  
  
 O `Stop` instrução suspende a execução, mas diferentemente `End`, ele não feche quaisquer arquivos ou desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).  
  
 Porque `End` encerra o aplicativo sem participação a qualquer recurso que pode ser aberto, você deve tentar encerrar corretamente antes de usá-lo. Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deve fechá-los antes de controle atingir o `End` instrução.  
  
 Você deve usar `End` com moderação e somente quando você precisa parar imediatamente. As maneiras normais para encerrar um procedimento ([instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) e [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas o fecham, mas também fornecem o código de chamada a oportunidade de corretamente. Um aplicativo de console, por exemplo, pode simplesmente `Return` do `Main` procedimento.  
  
> [!IMPORTANT]
>  O `End` chamadas de instrução o <xref:System.Environment.Exit%2A> método o <xref:System.Environment> classe no <xref:System> namespace. <xref:System.Environment.Exit%2A>requer que você tenha `UnmanagedCode` permissão. Se você não fizer isso, um <xref:System.Security.SecurityException> erro ocorre.  
  
 Quando seguido por uma palavra-chave adicional, [final \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento apropriado ou bloco. Por exemplo, `End Function` finaliza a definição de uma `Function` procedimento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `End` instrução para finalizar a execução de código se o usuário solicitar.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>Notas do desenvolvedor de dispositivo inteligente  
 Não há suporte para essa instrução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [Instrução Stop](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Final \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
