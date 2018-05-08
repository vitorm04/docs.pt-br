---
title: Tipos anônimos (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 451fe45c9b5efbeb64b1066d6ba8e5f9b27300c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-types-visual-basic"></a>Tipos anônimos (Visual Basic)
Visual Basic oferece suporte a tipos anônimos, que permitem que você crie objetos sem escrever uma definição de classe para o tipo de dados. Em vez disso, o compilador gera uma classe para você. A classe sem nome utilizável, herda diretamente da <xref:System.Object>e contém as propriedades que você especificar no declarar o objeto. Porque o nome do tipo de dados não for especificado, ele é chamado como uma *tipo anônimo*.  
  
 O exemplo a seguir declara e cria variável `product` como uma instância de um tipo anônimo que tem duas propriedades, `Name` e `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 Um *expressão de consulta* usa tipos anônimos para combinar as colunas de dados selecionados por uma consulta. Você não pode definir o tipo de resultado com antecedência, porque você não pode prever as colunas de que uma determinada consulta pode selecionar. Tipos anônimos permitem escrever uma consulta que seleciona qualquer número de colunas, em qualquer ordem. O compilador cria um tipo de dados que coincide com as propriedades especificadas e a ordem especificada.  
  
 Nos exemplos a seguir, `products` é uma lista de objetos do produto, cada um deles tem várias propriedades. Variável `namePriceQuery` contém a definição de uma consulta que, quando ele é executado, retorna uma coleção de instâncias de um tipo anônimo que tem duas propriedades, `Name` e `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 Variável `nameQuantityQuery` contém a definição de uma consulta que, quando ele é executado, retorna uma coleção de instâncias de um tipo anônimo que tem duas propriedades, `Name` e `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 Para obter mais informações sobre o código criado pelo compilador para um tipo anônimo, consulte [definição de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
>  O nome do tipo anônimo é compilador gerado e pode variar de compilação a compilação. O código não deve usar ou contar com o nome de um tipo anônimo, pois o nome pode ser alterado quando um projeto é recompilado.  
  
## <a name="declaring-an-anonymous-type"></a>Declarar um tipo anônimo  
 A declaração de uma instância de um tipo anônimo usa uma lista de inicializadores para especificar as propriedades do tipo. Você pode especificar somente propriedades quando você declara um tipo anônimo, não outros elementos de classe como métodos ou eventos. No exemplo a seguir, `product1` é uma instância de um tipo anônimo que tem duas propriedades: `Name` e `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 Se você designar propriedades como propriedades de chave, você pode usá-los para comparar duas instâncias de tipo anônimo para igualdade. No entanto, os valores das propriedades de chave não podem ser alterados. Consulte a seção Propriedades de chave mais adiante neste tópico para obter mais informações.  
  
 Observe que a declaração de uma instância de um tipo anônimo é como declarar uma instância de um tipo nomeado usando um inicializador de objeto:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 Para obter mais informações sobre outras maneiras para especificar propriedades de tipo anônimo, consulte [como: inferir nomes de propriedade e tipos de declarações de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Propriedades da chave  
 Propriedades de chave diferem de propriedades não-chave de várias maneiras fundamentais:  
  
-   Apenas os valores das propriedades de chave são comparados para determinar se duas instâncias são iguais.  
  
-   Os valores das propriedades de chave são somente leitura e não podem ser alterados.  
  
-   Somente valores de propriedade de chave são incluídos no algoritmo hash gerado pelo compilador de código para um tipo anônimo.  
  
### <a name="equality"></a>Igualdade  
 Instâncias de tipos anônimos podem ser iguais somente se estes forem instâncias do mesmo tipo anônimo. O compilador trata duas instâncias como instâncias do mesmo tipo, se eles atendem às seguintes condições:  
  
-   Eles são declarados no mesmo assembly.  
  
-   Suas propriedades têm os mesmos nomes, os mesmos tipos deduzidos e são declaradas na mesma ordem. Nome comparações não diferenciam maiusculas de minúsculas.  
  
-   As mesmas propriedades em cada são marcadas como propriedades de chave.  
  
-   Pelo menos uma propriedade em cada declaração é uma propriedade de chave.  
  
 Uma instância de um anônimo tipos que não tem nenhuma propriedade de chave é igual somente a mesmo.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 Duas instâncias do mesmo tipo anônimo são iguais se os valores de suas propriedades de chave são iguais. Os exemplos a seguir ilustram como igualdade é testada.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### <a name="read-only-values"></a>Valores somente leitura  
 Os valores das propriedades de chave não podem ser alterados. Por exemplo, em `prod8` no exemplo anterior, o `Name` e `Price` campos são `read-only`, mas `OnHand` pode ser alterado.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Tipos anônimos de expressões de consulta  
 Expressões de consulta nem sempre exigem a criação de tipos anônimos. Quando possível, eles usam um tipo existente para manter os dados da coluna. Isso ocorre quando a consulta retorna registros qualquer inteiros da fonte de dados, ou apenas um campo de cada registro. Nos exemplos de código a seguir, `customers` é uma coleção de objetos de um `Customer` classe. A classe tem várias propriedades, e você pode incluir um ou mais no resultado da consulta, em qualquer ordem. Nos dois primeiros exemplos, não anônimos tipos são necessários porque as consultas selecionam elementos de tipos nomeados:  
  
-   `custs1` contém uma coleção de cadeias de caracteres, porque `cust.Name` é uma cadeia de caracteres.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   `custs2` contém uma coleção de `Customer` objetos, porque cada elemento do `customers` é um `Customer` objeto e o elemento inteiro é selecionado pela consulta.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 No entanto, tipos nomeados apropriados não estão sempre disponíveis. Você talvez queira selecionar nomes de clientes e endereços para uma finalidade, números de identificação de cliente e locais para outro e nomes de clientes, endereços e históricos pedido para um terceiro. Tipos anônimos permitem que você selecionar qualquer combinação de propriedades, em qualquer ordem, sem primeiro declarar um novo tipo nomeado para armazenar o resultado. Em vez disso, o compilador cria um tipo anônimo para cada compilação de propriedades. A consulta a seguir seleciona somente o cliente nome e número de identificação de cada `Customer` objeto `customers`. Portanto, o compilador cria um tipo anônimo que contém somente essas duas propriedades.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 Os nomes e os tipos de dados das propriedades no tipo anônimo são tirados dos argumentos para `Select`, `cust.Name` e `cust.ID`. As propriedades em um tipo anônimo que é criado por uma consulta são sempre propriedades de chave. Quando `custs3` é executado no seguinte `For Each` loop, o resultado é uma coleção de instâncias de um tipo anônimo com duas propriedades chave, `Name` e `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 Os elementos da coleção representado por `custs3` são fortemente tipadas, e você pode usar o IntelliSense para navegar através das propriedades disponíveis e para verificar seus tipos.  
  
 Para obter mais informações, consulte [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Decidir se deve usar tipos anônimos  
 Antes de criar um objeto como uma instância de uma classe anônima, considere se que é a melhor opção. Por exemplo, se você deseja criar um objeto temporário para conter dados relacionados, e não há necessidade de outros campos e métodos que pode conter uma classe completa, um tipo anônimo é uma boa solução. Tipos anônimos são também convenientes se você quiser uma seleção diferente de propriedades para cada declaração, ou se você quiser alterar a ordem das propriedades. No entanto, se seu projeto inclui vários objetos que têm as mesmas propriedades, em uma ordem fixa, você pode declará-los mais facilmente usando um tipo nomeado com um construtor de classe. Por exemplo, com um construtor apropriado, é mais fácil declarar várias instâncias de um `Product` classe que ele é para declarar várias instâncias de um tipo anônimo.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 Outra vantagem dos tipos nomeados é que o compilador pode pegar um acidental digitação incorreta de um nome de propriedade. Nos exemplos anteriores, `firstProd2`, `secondProd2`, e `thirdProd2` devem ser instâncias do mesmo tipo anônimo. No entanto, se você fosse acidentalmente declarar `thirdProd2` em uma das maneiras a seguir, seu tipo deve ser diferente do `firstProd2` e `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 Além disso, há limitações no uso de tipos anônimos que não se aplicam às instâncias dos tipos nomeados. `firstProd2`, `secondProd2`, e `thirdProd2` são instâncias do mesmo tipo anônimo. No entanto, o nome para o tipo anônimo compartilhado não está disponível e não pode aparecer em um nome de tipo é esperado no seu código. Por exemplo, um tipo anônimo não pode ser usado para definir uma assinatura de método para declarar a outra variável ou campo ou em qualquer declaração de tipo. Como resultado, tipos anônimos não são apropriados quando você precisa compartilhar informações entre os métodos.  
  
## <a name="an-anonymous-type-definition"></a>Uma definição de tipo anônimo  
 Em resposta à declaração de uma instância de um tipo anônimo, o compilador cria uma nova definição de classe que contém as propriedades especificadas.  
  
 Se o tipo anônimo contém pelo menos uma propriedade de chave, a definição substitui três membros herdados <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, e <xref:System.Object.ToString%2A>. O código produzido para testar a igualdade e determinar que o valor de código hash considera apenas as propriedades de chave. Se o tipo anônimo contiver sem propriedades chave, somente <xref:System.Object.ToString%2A> é substituído. Propriedades explicitamente nomeadas de um tipo anônimo não podem entrar em conflito com esses métodos gerados. Ou seja, você não pode usar `.Equals`, `.GetHashCode`, ou `.ToString` para uma propriedade de nome.  
  
 Definições de tipo anônimo que tenham pelo menos uma propriedade de chave também implementa o <xref:System.IEquatable%601?displayProperty=nameWithType> interface, onde `T` é o tipo do tipo anônimo.  
  
 Para obter mais informações sobre o código criado pelo compilador e a funcionalidade dos métodos substituídos, consulte [definição de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Definição do Tipo Anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Chave](../../../../visual-basic/language-reference/modifiers/key.md)
