---
title: Tipo de lista (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
dev_langs:
- VB
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters, type
- constraints, Structure keyword
- type parameters, constraints
- types [Visual Basic], generic
- parameters, generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: 33
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9475140121d51f6096a9de8996ca8ef211cdec99
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

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
|`genericmodifier`|Opcional. Pode ser usado somente em interfaces e delegados genéricos. Você pode declarar um tipo covariant usando o [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) palavra-chave ou contravariant usando o [na](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) palavra-chave. Consulte [covariância e contravariância](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8).|  
|`typename`|Necessário. Nome do parâmetro de tipo. Isso é um espaço reservado, a ser substituído por um tipo definido fornecido pelo argumento de tipo correspondente.|  
|`constraintlist`|Opcional. Lista de requisitos que restringe o tipo de dados que pode ser fornecido para `typename`. Se você tiver várias restrições, coloque-as entre chaves (`{ }`) e separe-as com vírgulas. Você deve apresentar a lista de restrições com a [como](../../../visual-basic/language-reference/statements/as-clause.md) palavra-chave. Você usa `As` apenas uma vez, no início da lista.|  
  
## <a name="remarks"></a>Comentários  
 Cada elemento de programação genérico deve executar pelo menos um parâmetro de tipo. Um parâmetro de tipo é um espaço reservado para um tipo específico (um *elemento construído*) que o código do cliente especifica quando ele cria uma instância do tipo genérico. Você pode definir uma classe genérica, estrutura, interface, procedimento ou delegado.  
  
 Para obter mais informações sobre quando definir um tipo genérico, consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md). Para obter mais informações sobre nomes de parâmetro de tipo, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Regras  
  
-   **Parênteses.** Se você fornecer uma lista de parâmetros de tipo, você deve colocá-la entre parênteses e você deve apresentar a lista com o [de](../../../visual-basic/language-reference/statements/of-clause.md) palavra-chave. Você usa `Of` apenas uma vez, no início da lista.  
  
-   **Restrições.** Uma lista de *restrições* em um tipo de parâmetro pode incluir os seguintes itens em qualquer combinação:  
  
    -   Qualquer número de interfaces. O tipo fornecido deve implementar cada interface nessa lista.  
  
    -   No máximo uma classe. O tipo fornecido deve herdar dessa classe.  
  
    -   A palavra-chave `New`. O tipo fornecido deve expor um construtor sem parâmetros que pode acessar o tipo genérico. Isso é útil se você restringir um parâmetro de tipo por uma ou mais interfaces. Um tipo que implementa interfaces não necessariamente expõe um construtor, e dependendo do nível de acesso de um construtor, o código dentro de tipo genérico pode não ser capaz de acessá-lo.  
  
    -   Ambos os `Class` palavra-chave ou o `Structure` palavra-chave. O `Class` palavra-chave restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele ser um tipo de referência, por exemplo uma cadeia de caracteres, matriz ou delegado, ou um objeto criado a partir de uma classe. O `Structure` palavra-chave restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele seja um tipo de valor, por exemplo, uma estrutura, enumeração ou dados elementar digite. Você não pode incluir `Class` e `Structure` no mesmo `constraintlist`.  
  
     O tipo fornecido deve satisfazer cada requisito que você incluir em `constraintlist`.  
  
     Restrições em cada parâmetro de tipo são independentes de restrições em outros parâmetros de tipo.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Substituição em tempo de compilação.** Quando você cria um tipo construído de um elemento de programação genérico, você fornece um tipo definido para cada parâmetro de tipo. O compilador Visual Basic substitui esse tipo fornecido para cada ocorrência de `typename` dentro do elemento genérico.  
  
-   **Ausência de restrições.** Se você não especificar quaisquer restrições em um parâmetro de tipo, seu código está limitado às operações e membros com suporte a [tipo de dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md) para esse parâmetro de tipo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma definição de uma classe de dicionário genérica, incluindo uma função reduzida para adicionar uma nova entrada ao dicionário.  
  
 [!code-vb[VbVbalrStatements n º&3;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a>Exemplo  
 Porque `dictionary` é genérico, o código que o usa pode criar uma variedade de objetos, cada um tendo a mesma funcionalidade mas agindo em um tipo de dados diferente. O exemplo a seguir mostra uma linha de código que cria um `dictionary` o objeto com `String` entradas e `Integer` chaves.  
  
 [!code-vb[VbVbalrStatements n º&4;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a definição reduzida equivalente gerada pelo exemplo anterior.  
  
 [!code-vb[VbVbalrStatements n º&5;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [De](../../../visual-basic/language-reference/statements/of-clause.md)   
 [Novo operador](../../../visual-basic/language-reference/operators/new-operator.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Tipo de dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Como: usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Covariância e contravariância](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8)   
 [Em](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)

