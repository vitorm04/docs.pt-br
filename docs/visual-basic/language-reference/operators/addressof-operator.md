---
title: Operador AddressOf
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350277"
---
# <a name="addressof-operator-visual-basic"></a>Operador AddressOf (Visual Basic)
Cria uma instância delegada que faz referência ao procedimento específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Partes  
 `procedurename`  
 Necessário. Especifica o procedimento a ser referenciado pelo delegado recém-criado.  
  
## <a name="remarks"></a>Comentários  
 O operador `AddressOf` cria um delegado que aponta para a sub-rotina ou função especificada por `procedurename`. Quando o procedimento especificado é um método de instância, o delegado se refere à instância e ao método. Em seguida, quando o delegado é invocado, o método especificado da instância especificada é chamado.  
  
 O operador `AddressOf` pode ser usado como o operando de um construtor delegate ou pode ser usado em um contexto no qual o tipo do delegado pode ser determinado pelo compilador.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o operador `AddressOf` para designar um delegado para manipular o evento `Click` de um botão.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `AddressOf` para designar a função de inicialização para um thread.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
