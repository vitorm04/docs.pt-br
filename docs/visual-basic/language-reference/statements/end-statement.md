---
title: Instrução End
ms.date: 07/20/2015
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
ms.openlocfilehash: 864ac5ef1713f8ffa93c18accede8ecd5b3b7a8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604415"
---
# <a name="end-statement"></a>Instrução End
Finaliza a execução imediatamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
End  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar o `End` instrução em qualquer lugar em um procedimento para forçar o aplicativo inteiro para interromper a execução. `End` Fecha todos os arquivos abertos com um `Open` instrução e limpa todas as variáveis do aplicativo. O aplicativo fecha assim que existem em outros programas que contenham referências a seus objetos e nenhum dos seu código está em execução.  
  
> [!NOTE]
>  O `End` instrução interrompe a execução de código abruptamente e não chama o `Dispose` ou `Finalize` método ou qualquer outro código do Visual Basic. Referências a objetos mantidas por outros programas são invalidadas. Se um `End` instrução for encontrada dentro de um `Try` ou `Catch` bloco, o controle passará para o correspondente `Finally` bloco.  
  
 O `Stop` instrução suspende a execução, mas diferentemente `End`, ele não feche quaisquer arquivos ou desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).  
  
 Porque `End` encerra o aplicativo sem participação a qualquer recurso que pode ser aberto, você deve tentar encerrar corretamente antes de usá-lo. Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deve fechá-los antes de controle atingir o `End` instrução.  
  
 Você deve usar `End` com moderação e somente quando você precisa parar imediatamente. As maneiras normais para encerrar um procedimento ([instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) e [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas o fecham, mas também fornecem o código de chamada a oportunidade de corretamente. Um aplicativo de console, por exemplo, pode simplesmente `Return` do `Main` procedimento.  
  
> [!IMPORTANT]
>  O `End` chamadas de instrução o <xref:System.Environment.Exit%2A> método o <xref:System.Environment> classe no <xref:System> namespace. <xref:System.Environment.Exit%2A> requer que você tenha `UnmanagedCode` permissão. Se você não fizer isso, um <xref:System.Security.SecurityException> erro ocorre.  
  
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
