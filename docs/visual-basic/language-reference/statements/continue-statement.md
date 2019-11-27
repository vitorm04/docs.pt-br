---
title: Instrução Continue
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354117"
---
# <a name="continue-statement-visual-basic"></a>Instrução Continue (Visual Basic)
Transfere o controle imediatamente para a próxima iteração de um loop.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode transferir de dentro de um loop `Do`, `For`ou `While` para a próxima iteração desse loop. O controle passa imediatamente para o teste de condição de loop, que é equivalente a transferir para a instrução `For` ou `While` ou para a instrução `Do` ou `Loop` que contém a cláusula `Until` ou `While`.  
  
 Você pode usar `Continue` em qualquer local no loop que permita transferências. As regras que permitem a transferência de controle são as mesmas que a [instrução goto](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Por exemplo, se um loop estiver totalmente contido em um bloco de `Try`, um bloco de `Catch` ou um bloco de `Finally`, você poderá usar `Continue` para transferir para fora do loop. Se, por outro lado, a estrutura `Try`...`End Try` estiver contida no loop, você não poderá usar `Continue` para transferir o controle do bloco de `Finally` e poderá usá-lo para transferir para fora de um bloco `Try` ou `Catch` somente se você transferir completamente da estrutura `Try`...`End Try`.  
  
 Se você tiver loops aninhados do mesmo tipo, por exemplo um loop de `Do` dentro de outro loop `Do`, uma instrução `Continue Do` ignorará a próxima iteração do loop de `Do` mais interno que a contém. Você não pode usar `Continue` para ignorar a próxima iteração de um loop de contenção do mesmo tipo.  
  
 Se você tiver loops aninhados de tipos diferentes, por exemplo, um loop de `Do` em um loop de `For`, poderá pular para a próxima iteração de qualquer um dos loops usando `Continue Do` ou `Continue For`.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir usa a instrução `Continue While` para pular para a próxima coluna de uma matriz se um divisor for zero. O `Continue While` está dentro de um loop de `For`. Ele transfere para a instrução `While col < lastcol`, que é a próxima iteração do loop de `While` mais interno que contém o loop de `For`.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
