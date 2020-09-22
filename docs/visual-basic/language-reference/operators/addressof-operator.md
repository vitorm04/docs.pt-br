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
ms.openlocfilehash: edce7d4a2268bd311045ea4972672fe8fd2600ea
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874886"
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

 O `AddressOf` operador cria um delegado que aponta para a sub-rotina ou função especificada por `procedurename` . Quando o procedimento especificado é um método de instância, o delegado se refere à instância e ao método. Em seguida, quando o delegado é invocado, o método especificado da instância especificada é chamado.  
  
 O `AddressOf` operador pode ser usado como o operando de um construtor delegado ou pode ser usado em um contexto no qual o tipo do delegado possa ser determinado pelo compilador.  
  
## <a name="example"></a>Exemplo  

 Este exemplo usa o `AddressOf` operador para designar um delegado para manipular o `Click` evento de um botão.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir usa o `AddressOf` operador para designar a função de inicialização para um thread.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Confira também

- [Instrução Declare](../statements/declare-statement.md)
- [Instrução Function](../statements/function-statement.md)
- [Instrução Sub](../statements/sub-statement.md)
- [Representantes](../../programming-guide/language-features/delegates/index.md)
