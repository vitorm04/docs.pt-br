---
title: "Lista de tipos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StructureConstraint"
  - "vb.StructureConstraint"
  - "ClassConstraint"
  - "vb.ClassConstraint"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "restrição de classe"
  - "restrições, palavra-chave Class"
  - "restrições, parâmetros de tipo in"
  - "restrições, palavra-chave Structure"
  - "restrições, tipos genéricos do Visual Basic"
  - "parâmetros genéricos"
  - "genéricos [Visual Basic], restrições"
  - "genéricos [Visual Basic], tipos genéricos"
  - "genéricos [Visual Basic], lista de tipos"
  - "genéricos [Visual Basic], parâmetros de tipo"
  - "parâmetros, genérico"
  - "parâmetros, Tipo "
  - "restrição de estrutura"
  - "parâmetros de tipo"
  - "parâmetros de tipo, restrições"
  - "tipos [Visual Basic], genérico"
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lista de tipos (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica os  *parâmetros de tipo*  para um elemento de programação *Generic*.  Múltiplos parâmetros são separados por vírgulas.  A seguir está a sintaxe de um parâmetro de tipo.  
  
## Sintaxe  
  
```  
  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`genericmodifier`|Opcional.  Pode ser usado apenas em delegados e interfaces genéricas.  Você pode declarar um tipo covariant usando o  [Check\-Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) palavra\-chave ou contravariant usando o  [na](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) palavra\-chave.  Consulte [Covariância e contravariância](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md).|  
|`typename`|Obrigatório.  Nome do parâmetro de tipo.  Este é um espaço reservado, a ser substituído por um tipo definido fornecido pelo argumento de tipo correspondente.|  
|`constraintlist`|Opcional.  Lista de requisitos que restringe o tipo de dados que pode ser fornecido para `typename`.  Se você tiver várias restrições, coloque\-as entre chaves \(`{ }`\) e separe\-as com vírgulas.  Você deve apresentar a lista de restrições com a palavra\-chave [As](../../../visual-basic/language-reference/statements/as-clause.md).  Você usa `As` somente uma vez, no início da lista.|  
  
## Comentários  
 Todo elemento de programação genérico deve receber pelo menso um parâmetro de tipo.  Um parâmetro de tipo é um espaço reservado para um tipo específico \(um  *elemento construído* \)que o código do cliente especifica quando ele cria uma instância do tipo genérico.  Você pode definir uma classe, estrutura, Interface, procedimento ou delegado genéricos.  
  
 Para obter mais informações sobre quando definir uma tipo genérico, consulte [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  Para obter mais informações sobre nomes de parâmetro de tipo, consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## Regras  
  
-   **Entre parênteses.** Se você fornecer uma lista de parâmetros de tipo, coloque\-o entre parênteses e você deve introduzir a lista com o  [de](../../../visual-basic/language-reference/statements/of-clause.md) palavra\-chave.  Você usa `Of` somente uma vez, no início da lista.  
  
-   **Restrições.** Uma lista de  *restrições* em um tipo de parâmetro pode incluir os seguintes itens em qualquer combinação:  
  
    -   Qualquer número de interfaces.  O tipo fornecido deve implementar todas as interfaces nessa lista.  
  
    -   No máximo uma classe.  O tipo fornecido deve herdar dessa classe.  
  
    -   A  palavra\-chave `New`.  O tipo fornecido deve expor um construtor sem\-parâmetros que pode ser acessado pelo seu tipo genérico.  Isso é útil se você restringir um parâmetro de tipo por uma ou mais interfaces.  Um tipo que implementa interfaces não necessariamente expõe um construtor, e dependendo do nível de acesso de um construtor, o código dentro de tipo genérico pode não poderá acessá\-lo.  
  
    -   Ou palavra\-chave `Class` ou a palavra\-chave `Structure`.  O `Class` palavra\-chave restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele ser um tipo de referência, por exemplo uma seqüência de caracteres, matriz ou representante, ou um objeto criado a partir de uma classe.  O `Structure` palavra\-chave restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele seja um tipo de valor, por exemplo uma estrutura, enumeração ou dados elementar digite.  Não é possível incluir ambos `Class` e `Structure` na mesma `constraintlist`.  
  
     O tipo fornecido deve satisfazer cada requisito que você incluiu na `constraintlist`.  
  
     Restrições sobre cada parâmetro de tipo são independentes de restrições em outros parâmetros de tipo.  
  
## Comportamento  
  
-   **Substituição em tempo de compilação.** Quando você cria um tipo construído de um elemento de programação genérico, você fornece um tipo definido para cada parâmetro de tipo.  O compilador Visual Basic substitui esse tipo fornecido para cada ocorrência de `typename` dentro do elemento genérico.  
  
-   **Ausência de restrições.** Se você não especificar quaisquer restrições em um parâmetro de tipo, seu código é limitado para as operações e os membros suportados pelo [Tipo de dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md) para esse parâmetro de tipo.  
  
## Exemplo  
 O exemplo a seguir mostra uma definição reduzida de uma classe Dicionário genérica, incluindo uma função reduzida para adicionar uma nova entrada ao dicionário.  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/type-list_1.vb)]  
  
## Exemplo  
 Porque `dictionary`é genérico ,o código que o usa pode criar uma variedade de objetos a partir dele, cada um tendo a mesma funcionalidade mas agindo em um tipo de dados diferente.  O exemplo a seguir mostra uma linha de código que cria um objeto `dictionary` com entradas `String` e chaves `Integer`.  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/type-list_2.vb)]  
  
## Exemplo  
 O exemplo a seguir mostra a definição reduzida equivalente gerada pelo exemplo anterior.  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/type-list_3.vb)]  
  
## Consulte também  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [Operador New](../../../visual-basic/language-reference/operators/new-operator.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Tipo de dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Covariância e contravariância](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)