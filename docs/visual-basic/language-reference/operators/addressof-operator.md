---
title: Operador AddressOf (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
dev_langs:
- VB
helpviewer_keywords:
- AddressOf operator
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
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
ms.openlocfilehash: 04a7c5be9b890faea561c28715093a271cf9eaa8
ms.lasthandoff: 03/13/2017

---
# <a name="addressof-operator-visual-basic"></a>Operador AddressOf (Visual Basic)
Cria uma instância delegada de procedimento que referencia o procedimento específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Partes  
 `procedurename`  
 Necessário. Especifica o procedimento a ser referenciado pelo delegado de procedimento recém-criado.  
  
## <a name="remarks"></a>Comentários  
 O `AddressOf` operador cria um delegado de função que aponta para a função especificada por `procedurename`. Quando o procedimento especificado é que um método de instância, em seguida, o delegado de função refere-se a instância e o método. Em seguida, quando o delegado de função é chamado o método especificado da instância especificada é chamado.  
  
 O `AddressOf` operador pode ser usado como o operando do construtor delegado ou pode ser usado em um contexto no qual o tipo do delegado pode ser determinado pelo compilador.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `AddressOf` operador para designar um delegado para manipular o `Click` eventos de um botão.  
  
 [!code-vb[VbVbalrDelegates n º&8;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `AddressOf` operador para designar a função de inicialização para um thread.  
  
 [!code-vb[VbVbalrDelegates n º&9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
