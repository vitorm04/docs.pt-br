---
title: Operador New (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 36cf71529b1f81c27881638d788117222c37171d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955879"
---
# <a name="new-operator-visual-basic"></a>Operador New (Visual Basic)
Apresenta uma `New` cláusula para criar uma nova instância de objeto, especifica uma restrição de Construtor em um parâmetro de tipo ou `Sub` identifica um procedimento como um construtor de classe.  
  
## <a name="remarks"></a>Comentários  
 Em uma declaração ou instrução de atribuição, `New` uma cláusula deve especificar uma classe definida da qual a instância pode ser criada. Isso significa que a classe deve expor um ou mais construtores que o código de chamada pode acessar.  
  
 Você pode usar uma `New` cláusula em uma instrução de declaração ou uma instrução de atribuição. Quando a instrução é executada, ela chama o construtor apropriado da classe especificada, passando os argumentos que você forneceu. O exemplo a seguir demonstra isso criando instâncias de uma `Customer` classe que tem dois construtores, um que não usa parâmetros e um que usa um parâmetro de cadeia de caracteres.  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 Como as matrizes são `New` classes, o pode criar uma nova instância de matriz, conforme mostrado nos exemplos a seguir.  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 O Common Language Runtime (CLR) gera um <xref:System.OutOfMemoryException> erro se não houver memória suficiente para criar a nova instância.  
  
> [!NOTE]
> A `New` palavra-chave também é usada em listas de parâmetros de tipo para especificar que o tipo fornecido deve expor um construtor acessível sem parâmetros. Para obter mais informações sobre parâmetros de tipo e restrições, consulte [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Para criar um procedimento de construtor para uma classe, defina o nome de `Sub` um procedimento para `New` a palavra-chave. Para obter mais informações, [consulte tempo de vida do objeto: Como os objetos são criados e](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)destruídos.  
  
 A `New` palavra-chave pode ser usada nesses contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.OutOfMemoryException>
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tempo de vida do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
