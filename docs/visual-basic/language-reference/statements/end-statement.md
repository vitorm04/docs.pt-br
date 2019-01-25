---
title: Instrução End (Visual Basic)
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
ms.openlocfilehash: a2c211e5ebfd00a639644243312cbe25f71f4cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593700"
---
# <a name="end-statement"></a>Instrução End
Finaliza a execução imediatamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
End  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar o `End` instrução em qualquer lugar em um procedimento para forçar o aplicativo inteiro para parar a execução. `End` Fecha todos os arquivos abertos com uma `Open` instrução e limpa todas as variáveis do aplicativo. O aplicativo é fechado assim que há outros programas que contenham referências a seus objetos e nenhum dos seu código está em execução.  
  
> [!NOTE]
>  O `End` instrução interrompe a execução de código abruptamente e não chama o `Dispose` ou `Finalize` método ou qualquer outro código do Visual Basic. Referências a objetos mantidas por outros programas serão invalidadas. Se um `End` instrução é encontrada dentro de uma `Try` ou `Catch` bloco, o controle não passa para os respectivos `Finally` bloco.  
  
 O `Stop` instrução suspende a execução, mas ao contrário `End`, não feche quaisquer arquivos ou desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).  
  
 Porque `End` encerra o aplicativo sem participação a qualquer recurso que pode ser aberto, você deve tentar encerrar corretamente antes de usá-lo. Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deve fechá-los antes de controle atinge a `End` instrução.  
  
 Você deve usar `End` com parcimônia e somente quando precisar parar imediatamente. As maneiras normais usadas para encerrar um procedimento ([instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) e [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas o fecham, mas também fornecem o código de chamada a oportunidade de corretamente. Um aplicativo de console, por exemplo, pode simplesmente `Return` do `Main` procedimento.  
  
> [!IMPORTANT]
>  O `End` instrução chama o <xref:System.Environment.Exit%2A> método da <xref:System.Environment> classe no <xref:System> namespace. <xref:System.Environment.Exit%2A> exige que você tenha `UnmanagedCode` permissão. Se você não fizer isso, um <xref:System.Security.SecurityException> erro ocorre.  
  
 Quando seguido por uma palavra-chave adicional, [final \<palavra-chave > demonstrativo](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento apropriado ou bloco. Por exemplo, `End Function` finaliza a definição de um `Function` procedimento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `End` instrução para finalizar a execução de código se o usuário solicitar.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>Notas do desenvolvedor de dispositivo inteligente  
 Não há suporte para essa instrução.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Instrução Stop](../../../visual-basic/language-reference/statements/stop-statement.md)
- [End \<palavra-chave > demonstrativo](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
