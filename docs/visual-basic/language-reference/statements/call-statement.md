---
title: Instrução Call (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a>Instrução Call (Visual Basic)
Transfere o controle para um `Function`, `Sub`, ou um procedimento de biblioteca de vínculo dinâmico (DLL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Partes  
 `procedureName`  
 Necessário. Nome do procedimento a ser chamado.  
  
 `argumentList`  
 Opcional. Lista de variáveis ou expressões representando os argumentos que são passados ao procedimento quando ele é chamado. Vários argumentos são separados por vírgulas. Se você incluir `argumentList`, coloque-o entre parênteses.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Call` palavra-chave quando você chama um procedimento. Para a maioria das chamadas de procedimento, não é necessário usar a palavra-chave.  
  
 Você normalmente usa o `Call` palavra-chave quando a expressão de chamada não começa com um identificador. Usar o `Call` palavra-chave para outros usos não é recomendado.  
  
 Se o procedimento retorna um valor, o `Call` instrução descarta.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra dois exemplos em que o `Call` palavra-chave é necessária chamar um procedimento. Nos dois exemplos, a expressão de chamada não foi iniciada com um identificador.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
