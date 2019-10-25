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
ms.openlocfilehash: c0870f4b056658a22928769c369024cdda24f354
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799041"
---
# <a name="new-operator-visual-basic"></a>Operador New (Visual Basic)

Apresenta uma cláusula `New` para criar uma nova instância de objeto, especifica uma restrição de Construtor em um parâmetro de tipo ou identifica um procedimento de `Sub` como um construtor de classe.

## <a name="remarks"></a>Comentários

Em uma declaração ou instrução de atribuição, uma cláusula `New` deve especificar uma classe definida da qual a instância pode ser criada. Isso significa que a classe deve expor um ou mais construtores que o código de chamada pode acessar.

Você pode usar uma cláusula `New` em uma instrução de declaração ou uma instrução de atribuição. Quando a instrução é executada, ela chama o construtor apropriado da classe especificada, passando os argumentos que você forneceu. O exemplo a seguir demonstra isso criando instâncias de uma `Customer` classe que tem dois construtores, um que não usa parâmetros e um que usa um parâmetro de cadeia de caracteres:

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

Como as matrizes são classes, `New` pode criar uma nova instância de matriz, conforme mostrado no exemplo a seguir:

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

O Common Language Runtime (CLR) gera um erro de <xref:System.OutOfMemoryException> se não houver memória suficiente para criar a nova instância.

> [!NOTE]
> A palavra-chave `New` também é usada em listas de parâmetros de tipo para especificar que o tipo fornecido deve expor um construtor acessível sem parâmetros. Para obter mais informações sobre parâmetros de tipo e restrições, consulte [lista de tipos](../statements/type-list.md).

Para criar um procedimento de construtor para uma classe, defina o nome de um procedimento `Sub` para a palavra-chave `New`. Para obter mais informações, consulte [tempo de vida do objeto: como os objetos são criados e destruídos](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

A palavra-chave `New` pode ser usada nesses contextos:

- [Instrução Dim](../statements/dim-statement.md)
- [Of](../statements/of-clause.md)
- [Instrução Sub](../statements/sub-statement.md)

## <a name="see-also"></a>Consulte também

- <xref:System.OutOfMemoryException>
- [Palavras-chave](../keywords/index.md)
- [Lista de Tipos](../statements/type-list.md)
- [Tipos genéricos no Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Tempo de vida do objeto: como os objetos são criados e destruídos](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
