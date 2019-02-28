---
title: Operador AddressOf (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: b68d93009d2d297f8b8867fb8e79b26173a45095
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964658"
---
# <a name="addressof-operator-visual-basic"></a>Operador AddressOf (Visual Basic)
Cria uma instância de procedimento delegado que referencia o procedimento específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Partes  
 `procedurename`  
 Necessário. Especifica o procedimento a ser referenciado pelo delegado procedimento recém-criado.  
  
## <a name="remarks"></a>Comentários  
 O `AddressOf` operador cria um delegado de função que aponta para a função especificada por `procedurename`. Quando o procedimento especificado é que um método de instância, em seguida, o delegado de função refere-se para a instância e o método. Em seguida, quando o delegado de função é chamado o método especificado da instância especificada é chamado.  
  
 O `AddressOf` operador pode ser usado como o operando de um construtor delegate ou ele pode ser usado em um contexto no qual o tipo do delegado pode ser determinado pelo compilador.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `AddressOf` operador para designar um delegado para manipular o `Click` evento de um botão.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `AddressOf` operador para designar a função de inicialização para um thread.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Consulte também
- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
