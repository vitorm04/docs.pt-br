---
title: "Implementa a instrução | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Implements
- Implements
dev_langs:
- VB
helpviewer_keywords:
- Implements statement, syntax
- Implements statement
- interface implementation, Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 361cba891ab9ee97473df53dabb4ac8d0745da2f
ms.lasthandoff: 03/13/2017

---
# <a name="implements-statement"></a>Instrução Implements
Especifica uma ou mais interfaces, ou membros de interface, que devem ser implementados na classe ou definição de estrutura na qual ele aparece.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Partes  
 `interfacename`  
 Necessário. Uma interface cujas propriedades, procedimentos e eventos está para ser implementados por membros correspondentes na classe ou estrutura.  
  
 `interfacemember`  
 Necessário. O membro de uma interface que está sendo implementado.  
  
## <a name="remarks"></a>Comentários  
 Uma interface é uma coleção de protótipos que representa os membros (propriedades, procedimentos e eventos) encapsula a interface. Interfaces contêm somente as declarações de membros; classes e estruturas implementam esses membros. Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 O `Implements` instrução deve seguir imediatamente o `Class` ou `Structure` instrução.  
  
 Quando você implementa uma interface, você deve implementar todos os membros declarados na interface. Omitir qualquer membro é considerado um erro de sintaxe. Para implementar um membro individual, você deve especificar o [implementa](../../../visual-basic/language-reference/statements/implements-clause.md) palavra-chave (que é separada do `Implements` instrução) quando você declara o membro na classe ou estrutura. Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Classes podem usar [particular](../../../visual-basic/language-reference/modifiers/private.md) implementações de propriedades e procedimentos, mas esses membros são acessíveis somente chamando uma instância da classe implementada dentro de uma variável declarada para ser do tipo da interface.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `Implements` instrução para implementar membros de uma interface. Ele define uma interface nomeada `ICustomerInfo` com um evento, uma propriedade e um procedimento. A classe `customerInfo` implementa todos os membros definidos na interface.  
  
 [!code-vb[33 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 Observe que a classe `customerInfo` usa o `Implements` instrução em uma linha de código fonte separado para indicar que a classe implementa todos os membros do `ICustomerInfo` interface. Cada membro na classe usa a `Implements` palavra-chave como parte de sua declaração de membros para indicar que ele implementa o membro da interface.  
  
## <a name="example"></a>Exemplo  
 Os dois procedimentos a seguir mostram como usar a interface implementada no exemplo anterior. Para testar a implementação, adicione esses procedimentos no seu projeto e chame o `testImplements` procedimento.  
  
 [!code-vb[VbVbalrStatements&#34;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Implementa](../../../visual-basic/language-reference/statements/implements-clause.md)   
 [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
