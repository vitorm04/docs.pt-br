---
title: Operador AddressOf (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52560a2d9071373fd28f7aad2e485da08324656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="addressof-operator-visual-basic"></a>Operador AddressOf (Visual Basic)
Cria uma instância de delegado de procedimento que referencia o procedimento específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Partes  
 `procedurename`  
 Necessário. Especifica o procedimento a ser referenciado pelo delegado de procedimento recém-criado.  
  
## <a name="remarks"></a>Comentários  
 O `AddressOf` operador cria um delegado de função que aponta para a função especificada por `procedurename`. Quando o procedimento especificado é que um método de instância, em seguida, o delegado de função refere-se a instância e o método. Em seguida, quando o delegado de função é chamado o método especificado da instância especificada é chamado.  
  
 O `AddressOf` operador pode ser usado como o operando de um construtor delegado, ou ele pode ser usado em um contexto no qual o tipo do delegado pode ser determinado pelo compilador.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `AddressOf` operador para designar um delegado para manipular o `Click` evento de um botão.  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `AddressOf` operador para designar a função de inicialização para um thread.  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
