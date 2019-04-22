---
title: Lista de tipos (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: d071e59d94e51ca55167983d0ee3098bd5c7dd8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843624"
---
# <a name="type-list-visual-basic"></a>Lista de tipos (Visual Basic)
Especifica o *parâmetros de tipo* para um *genérico* elemento de programação. Vários parâmetros são separados por vírgulas. A seguir está a sintaxe para um parâmetro de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`genericmodifier`|Opcional. Pode ser usado somente em interfaces e delegados genéricos. Você pode declarar um tipo de covariante usando o [horizontalmente](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) palavra-chave ou contravariante usando a [em](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) palavra-chave. Consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).|  
|`typename`|Necessário. Nome do parâmetro de tipo. Isso é um espaço reservado, a ser substituído por um tipo definido fornecido pelo argumento de tipo correspondente.|  
|`constraintlist`|Opcional. Lista de requisitos que restringe o tipo de dados que pode ser fornecido para `typename`. Se você tiver várias restrições, coloque-as entre chaves (`{ }`) e separe-as com vírgulas. Você deve apresentar a lista de restrições com o [como](../../../visual-basic/language-reference/statements/as-clause.md) palavra-chave. Você usa `As` apenas uma vez, no início da lista.|  
  
## <a name="remarks"></a>Comentários  
 Cada elemento de programação genérico deve executar pelo menos um parâmetro de tipo. Um parâmetro de tipo é um espaço reservado para um tipo específico (um *elemento construído*) que o código de cliente especifica quando ele cria uma instância do tipo genérico. Você pode definir uma classe genérica, estrutura, interface, procedimento ou delegado.  
  
 Para obter mais informações sobre quando definir um tipo genérico, consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md). Para obter mais informações sobre nomes de parâmetro de tipo, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Regras  
  
-   **Parênteses.** Se você fornecer uma lista de parâmetros de tipo, você deve colocá-la entre parênteses e você deve apresentar a lista com o [de](../../../visual-basic/language-reference/statements/of-clause.md) palavra-chave. Você usa `Of` apenas uma vez, no início da lista.  
  
-   **Restrições.** Uma lista dos *restrições* em um tipo de parâmetro pode incluir os seguintes itens em qualquer combinação:  
  
    -   Qualquer número de interfaces. O tipo fornecido deve implementar cada interface nessa lista.  
  
    -   No máximo uma classe. O tipo fornecido deve herdar dessa classe.  
  
    -   A palavra-chave `New`. O tipo fornecido deve expor um construtor sem parâmetros que o tipo genérico pode acessar. Isso é útil se você restringir um parâmetro de tipo por uma ou mais interfaces. Um tipo que implementa as interfaces não necessariamente expõe um construtor e, dependendo do nível de acesso de um construtor, o código dentro de tipo genérico pode não ser capaz de acessá-lo.  
  
    -   Ambos os `Class` palavra-chave ou o `Structure` palavra-chave. O `Class` palavra-chave restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele ser um tipo de referência, por exemplo uma cadeia de caracteres, matriz ou delegado, ou um objeto criado de uma classe. O `Structure` palavra-chave restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele seja um tipo de valor, por exemplo, uma estrutura, enumeração ou dados elementar digite. Você não pode incluir ambos `Class` e `Structure` no mesmo `constraintlist`.  
  
     O tipo fornecido deve satisfazer todos os requisitos incluem no `constraintlist`.  
  
     Restrições em cada parâmetro de tipo são independentes de restrições em outros parâmetros de tipo.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Substituição de tempo de compilação.** Quando você cria um tipo construído de um elemento de programação genérico, você fornece um tipo definido para cada parâmetro de tipo. O compilador do Visual Basic substitui esse tipo fornecido para cada ocorrência de `typename` dentro do elemento genérico.  
  
-   **Ausência de restrições.** Se você não especificar todas as restrições em um parâmetro de tipo, seu código é limitado às operações e membros com suporte a [tipo de dados de objeto](../../../visual-basic/language-reference/data-types/object-data-type.md) para esse parâmetro de tipo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma definição de uma classe de dicionário genéricas, incluindo uma função em esqueleto para adicionar uma nova entrada ao dicionário.  
  
 [!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 Porque `dictionary` é genérico, o código que usa a ele pode criar uma variedade de objetos dele, cada um tendo a mesma funcionalidade mas agindo em outro tipo de dados. O exemplo a seguir mostra uma linha de código que cria uma `dictionary` do objeto com `String` entradas e `Integer` chaves.  
  
 [!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a definição de esqueleto equivalente gerada pelo exemplo anterior.  
  
 [!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Of](../../../visual-basic/language-reference/statements/of-clause.md)
- [Operador New](../../../visual-basic/language-reference/operators/new-operator.md)
- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Tipo de Dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Como: usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Covariância e Contravariância](../../programming-guide/concepts/covariance-contravariance/index.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Saída](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
