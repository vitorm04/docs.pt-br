---
title: Operador New (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a>Operador New (Visual Basic)
Apresenta um `New` cláusula para criar uma nova instância de objeto, especifica uma restrição de construtor em um parâmetro de tipo ou identifica um `Sub` procedimento como um construtor de classe.  
  
## <a name="remarks"></a>Comentários  
 Em uma declaração ou instrução de atribuição, um `New` cláusula deve especificar uma classe definida na qual a instância pode ser criada. Isso significa que a classe deve expor um ou mais construtores que pode acessar o código de chamada.  
  
 Você pode usar um `New` cláusula em uma instrução de declaração ou uma instrução de atribuição. Quando a instrução é executada, ele chama o construtor apropriado da classe especificada, passando quaisquer argumentos que você forneceu. O exemplo a seguir demonstra isso ao criar instâncias de um `Customer` classe que tem dois construtores, um que não usa nenhum parâmetro e outro que usa um parâmetro de cadeia de caracteres.  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 Como matrizes são classes, `New` pode criar uma nova instância de matriz, conforme mostrado nos exemplos a seguir.  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 O common language runtime (CLR) gera um <xref:System.OutOfMemoryException> erro se não houver memória suficiente para criar a nova instância.  
  
> [!NOTE]
>  O `New` palavra-chave também é usado em listas de parâmetros de tipo para especificar que o tipo fornecido deve expor um construtor acessível sem parâmetros. Para obter mais informações sobre os parâmetros de tipo e restrições, consulte [lista tipo](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Para criar um procedimento de construtor para uma classe, defina o nome de um `Sub` procedimento para o `New` palavra-chave. Para obter mais informações, consulte [vida útil do objeto: como os objetos são criados e Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 O `New` palavra-chave pode ser usada nesses contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.OutOfMemoryException>  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)  
 [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
