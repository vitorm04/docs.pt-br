---
title: Instrução Implements
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: e2e279b2c935dd082cbf832265a8ad09e6dffe9e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351148"
---
# <a name="implements-statement"></a>Instrução Implements
Especifica uma ou mais interfaces, ou membros de interface, que devem ser implementados na definição de classe ou estrutura na qual ele aparece.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Partes  
 `interfacename`  
 Necessária. Uma interface cujas propriedades, procedimentos e eventos devem ser implementados por membros correspondentes na classe ou estrutura.  
  
 `interfacemember`  
 Necessária. O membro de uma interface que está sendo implementada.  
  
## <a name="remarks"></a>Comentários  
 Uma interface é uma coleção de protótipos que representa os membros (Propriedades, procedimentos e eventos) que a interface encapsula. As interfaces contêm apenas as declarações para membros; classes e estruturas implementam esses membros. Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 A instrução `Implements` deve seguir imediatamente a instrução `Class` ou `Structure`.  
  
 Ao implementar uma interface, você deve implementar todos os membros declarados na interface. A omissão de qualquer membro é considerada um erro de sintaxe. Para implementar um membro individual, você especifica a palavra-chave [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) (que é separada da instrução `Implements`) quando você declara o membro na classe ou estrutura. Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 As classes podem usar implementações [privadas](../../../visual-basic/language-reference/modifiers/private.md) de propriedades e procedimentos, mas esses membros são acessíveis somente por meio da conversão de uma instância da classe de implementação em uma variável declarada para ser do tipo da interface.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a instrução `Implements` para implementar membros de uma interface. Ele define uma interface chamada `ICustomerInfo` com um evento, uma propriedade e um procedimento. A classe `customerInfo` implementa todos os membros definidos na interface.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Observe que a classe `customerInfo` usa a instrução `Implements` em uma linha de código-fonte separada para indicar que a classe implementa todos os membros da interface `ICustomerInfo`. Em seguida, cada membro na classe usa a palavra-chave `Implements` como parte de sua declaração de membro para indicar que ela implementa esse membro de interface.  
  
## <a name="example"></a>Exemplo  
 Os dois procedimentos a seguir mostram como você pode usar a interface implementada no exemplo anterior. Para testar a implementação, adicione esses procedimentos ao seu projeto e chame o procedimento de `testImplements`.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Consulte também

- [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)
- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
