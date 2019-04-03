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
ms.openlocfilehash: 630b0c48def77449f426b287a26f95af7cfb930e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837677"
---
# <a name="new-operator-visual-basic"></a>Operador New (Visual Basic)
Apresenta uma `New` cláusula para criar uma nova instância de objeto, especifica uma restrição de construtor em um parâmetro de tipo, ou identifica um `Sub` procedimento como um construtor de classe.  
  
## <a name="remarks"></a>Comentários  
 Em uma declaração ou instrução de atribuição, um `New` cláusula deve especificar uma classe definida do qual a instância pode ser criada. Isso significa que a classe deve expor um ou mais construtores que o código de chamada pode acessar.  
  
 Você pode usar um `New` cláusula em uma instrução de declaração ou uma instrução de atribuição. Quando a instrução é executado, ele chama o construtor apropriado da classe especificada, passando quaisquer argumentos fornecidos por você. O exemplo a seguir demonstra isso com a criação de instâncias de um `Customer` classe que tem dois construtores, um que não usa nenhum parâmetro e um que utiliza um parâmetro de cadeia de caracteres.  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 Uma vez que as matrizes são classes, `New` pode criar uma nova instância de matriz, conforme mostrado nos exemplos a seguir.  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 O common language runtime (CLR) lançará um <xref:System.OutOfMemoryException> erro se não houver memória suficiente para criar a nova instância.  
  
> [!NOTE]
>  O `New` palavra-chave também é usado em listas de parâmetros de tipo para especificar que o tipo fornecido deve expor um construtor sem parâmetros acessível. Para obter mais informações sobre parâmetros de tipo e restrições, consulte [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Para criar um procedimento de construtor para uma classe, defina o nome de um `Sub` procedimento para o `New` palavra-chave. Para obter mais informações, consulte [tempo de vida do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 O `New` palavra-chave pode ser usada nesses contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.OutOfMemoryException>
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tempo de vida do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
