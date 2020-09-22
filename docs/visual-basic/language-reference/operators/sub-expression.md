---
title: Subexpressão
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: e564fa3f717fc1a9f4e9961d9b3e961912a4d56b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873323"
---
# <a name="sub-expression-visual-basic"></a>Subexpressão (Visual Basic)

Declara os parâmetros e o código que definem uma expressão lambda de sub-rotina.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`parameterlist`|Opcional. Uma lista de nomes de variáveis locais que representam os parâmetros do procedimento. Os parênteses devem estar presentes mesmo quando a lista estiver vazia. Para obter mais informações, consulte [lista de parâmetros](../statements/parameter-list.md).|  
|`statement`|Necessário. Uma única instrução.|  
|`statements`|Necessário. Uma lista de instruções.|  
  
## <a name="remarks"></a>Comentários  

 Uma *expressão lambda* é uma sub-rotina que não tem um nome e que executa uma ou mais instruções. Você pode usar uma expressão lambda em qualquer lugar que possa usar um tipo delegado, exceto como um argumento para `RemoveHandler` . Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [instrução delegate](../statements/delegate-statement.md) e [conversão de delegado reduzida](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda  

 A sintaxe de uma expressão lambda é semelhante à de uma sub-rotina padrão. As diferenças são:  
  
- Uma expressão lambda não tem um nome.  
  
- Uma expressão lambda não pode ter um modificador, como `Overloads` ou `Overrides` .  
  
- O corpo de uma expressão lambda de linha única deve ser uma instrução, não uma expressão. O corpo pode consistir em uma chamada para um procedimento Sub, mas não uma chamada para um procedimento Function.  
  
- Em uma expressão lambda, todos os parâmetros devem ter tipos de dados especificados ou todos os parâmetros devem ser inferidos.  
  
- Parâmetros opcionais e `ParamArray` não são permitidos em expressões lambda.  
  
- Parâmetros genéricos não são permitidos em expressões lambda.  
  
## <a name="example"></a>Exemplo  

 Veja a seguir um exemplo de uma expressão lambda que grava um valor no console. O exemplo mostra a sintaxe de expressão lambda de linha única e de várias linhas para uma sub-rotina. Para obter mais exemplos, consulte [expressões lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Confira também

- [Instrução Sub](../statements/sub-statement.md)
- [Expressões lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Operadores e expressões](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Instruções](../../programming-guide/language-features/statements.md)
- [Conversão de delegado reduzida](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
