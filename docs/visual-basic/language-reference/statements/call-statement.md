---
title: Instrução Call
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 7de194ea23827e08c49f4519c1000708a4bd91b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350157"
---
# <a name="call-statement-visual-basic"></a>Instrução Call (Visual Basic)

Transfere o controle para um procedimento de `Function`, `Sub`ou DLL (biblioteca de vínculo dinâmico).  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Partes  

|||
|---|---|
|`procedureName`|Necessária. Nome do procedimento a ser chamado.|
|`argumentList`|Opcional. Lista de variáveis ou expressões que representam argumentos que são passados para o procedimento quando ele é chamado. Vários argumentos são separados por vírgulas. Se você incluir `argumentList`, deverá colocá-lo entre parênteses.|
|||
  
## <a name="remarks"></a>Comentários

 Você pode usar a palavra-chave `Call` ao chamar um procedimento. Para a maioria das chamadas de procedimento, você não precisa usar essa palavra-chave.

 Normalmente, você usa a palavra-chave `Call` quando a expressão chamada não começa com um identificador. O uso da palavra-chave `Call` para outros usos não é recomendado.

 Se o procedimento retornar um valor, a instrução `Call` o descartará.

## <a name="example"></a>Exemplo

 O código a seguir mostra dois exemplos em que a palavra-chave `Call` é necessária para chamar um procedimento. Em ambos os exemplos, a expressão chamada não começa com um identificador.

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Function](function-statement.md)
- [Instrução Sub](sub-statement.md)
- [Instrução Declare](declare-statement.md)
- [Expressões Lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
