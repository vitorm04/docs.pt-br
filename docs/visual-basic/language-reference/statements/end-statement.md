---
title: "Fim de instrução | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.End
- End
dev_langs:
- VB
helpviewer_keywords:
- execution, ending
- files, closing
- End keyword, End statements
- programs, quitting
- code, exiting
- program termination
- End statement
- execution, stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: 19
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
ms.openlocfilehash: 4c24e22271a9d380f4fadc9d7549c83e7273dbe9
ms.lasthandoff: 03/13/2017

---
# <a name="end-statement"></a>Instrução End
Finaliza a execução imediatamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
End  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar o `End` instrução em qualquer lugar em um procedimento para forçar o aplicativo inteiro para parar a execução. `End`Fecha todos os arquivos abertos com uma `Open` instrução e limpa todas as variáveis do aplicativo. O aplicativo fecha assim que há outros programas que contenham referências a seus objetos e nenhum dos seu código está em execução.  
  
> [!NOTE]
>  O `End` instrução interrompe a execução de código abruptamente e não chama o `Dispose` ou `Finalize` método ou qualquer outro código Visual Basic. Referências a objetos mantidas por outros programas são invalidadas. Se um `End` declaração for encontrada dentro de uma `Try` ou `Catch` bloco de controle não passa para o correspondente `Finally` bloco.  
  
 O `Stop` instrução suspende a execução, mas diferentemente `End`, ele não fecha os arquivos nem desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).  
  
 Porque `End` encerra o aplicativo sem participação a qualquer recurso que pode ser aberto, você deve tentar encerrar corretamente antes de usá-lo. Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deve fechá-los antes de controle atinge o `End` instrução.  
  
 Você deve usar `End` com parcimônia e somente quando você precisa parar imediatamente. As maneiras normais para encerrar um procedimento ([instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) e [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas o fecham, mas também fornecem o código de chamada a oportunidade de corretamente. Um aplicativo de console, por exemplo, pode simplesmente `Return` do `Main` procedimento.  
  
> [!IMPORTANT]
>  O `End` instrução chama o <xref:System.Environment.Exit%2A>método do <xref:System.Environment>classe o <xref:System>namespace.</xref:System> </xref:System.Environment> </xref:System.Environment.Exit%2A> <xref:System.Environment.Exit%2A>requer que você tenha `UnmanagedCode` permissão.</xref:System.Environment.Exit%2A> Se não, uma <xref:System.Security.SecurityException>ocorre erro.</xref:System.Security.SecurityException>  
  
 Quando seguido por uma palavra-chave adicional, [final \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento apropriado ou bloco. Por exemplo, `End Function` finaliza a definição de uma `Function` procedimento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `End` instrução para encerrar a execução de código se o usuário solicitar.  
  
 [!code-vb[VbVersHelp60Controls&#64;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>Anotações de desenvolvedor de dispositivo inteligente  
 Não há suporte para essa instrução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Permissions.SecurityPermissionFlag></xref:System.Security.Permissions.SecurityPermissionFlag>   
 [Instrução Stop](../../../visual-basic/language-reference/statements/stop-statement.md)   
 [End \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
