---
title: "Instrução Call (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Call
dev_langs:
- VB
helpviewer_keywords:
- procedures, Call statement
- Call statement
- procedures, calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 13
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7a5ad8422f133c0bb5da875deaeab6c1dab13028
ms.lasthandoff: 03/13/2017

---
# <a name="call-statement-visual-basic"></a>Instrução Call (Visual Basic)
Transfere o controle para uma `Function`, `Sub`, ou um procedimento de biblioteca de vínculo dinâmico (DLL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Partes  
 `procedureName`  
 Necessário. Nome do procedimento a ser chamado.  
  
 `argumentList`  
 Opcional. Lista de variáveis ou expressões que representa os argumentos que são passados para o procedimento quando é chamado. Vários argumentos são separados por vírgulas. Se você incluir `argumentList`, você deve colocá-la entre parênteses.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Call` palavra-chave quando você chama um procedimento. Para a maioria das chamadas de procedimento, não é necessário usar essa palavra-chave.  
  
 Você normalmente usa o `Call` palavra-chave quando a expressão de chamada não começa com um identificador. Usar o `Call` palavra-chave para outros usos não é recomendado.  
  
 Se o procedimento retorna um valor, o `Call` instrução descarta.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra dois exemplos onde a `Call` palavra-chave é necessária chamar um procedimento. Nos dois exemplos, a expressão de chamada não começa com um identificador.  
  
 [!code-vb[VbVbalrStatements&#97;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
