---
title: 'Inicializadores de objeto: tipos nomeados e anônimos (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 612b1dcea0f776dfd4580803e76f2785e7d28da6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655630"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Inicializadores de objeto: tipos nomeados e anônimos (Visual Basic)
Inicializadores de objeto permitem que você especifique propriedades para um objeto complexo usando uma única expressão. Eles podem ser usados para criar instâncias dos tipos nomeados e de tipos anônimos.  
  
## <a name="declarations"></a>Declarações  
 Declarações de instâncias de tipos nomeados e anônimos podem ser quase idênticas, mas seus efeitos não são iguais. Cada categoria tem capacidades e restrições de seu próprio. O exemplo a seguir mostra uma maneira conveniente de declarar e inicializar uma instância de uma classe nomeada, `Customer`, usando uma lista de inicializadores de objeto. Observe que o nome da classe é especificado após a palavra-chave `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 Um tipo anônimo não tem utilizável nome. Portanto, uma instanciação de um tipo anônimo não pode incluir um nome de classe.  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 Os requisitos e os resultados de duas declarações não são os mesmos. Para `namedCust`, um `Customer` classe que tem um `Name` propriedade já deve existir e a declaração cria uma instância dessa classe. Para `anonymousCust`, o compilador define uma nova classe que tem uma propriedade, uma cadeia de caracteres chamada `Name`e cria uma nova instância da classe.  
  
## <a name="named-types"></a>Tipos nomeados  
 Inicializadores de objeto fornecem uma maneira simple para chamar o construtor de tipo e, em seguida, defina os valores de algumas ou todas as propriedades em uma única instrução. O compilador chama o construtor apropriado para a instrução: o construtor padrão se nenhum argumento é apresentado ou um construtor com parâmetros, se um ou mais argumentos forem enviados. Depois disso, as propriedades especificadas são inicializadas na ordem em que são apresentados na lista de inicializador.  
  
 Consiste em cada inicialização na lista de inicializador da atribuição de um valor inicial para um membro da classe. Os nomes e tipos de dados dos membros são determinados quando a classe é definida. Nos exemplos a seguir, o `Customer` classe deve existir e devem ter membros nomeado `Name` e `City` que pode aceitar valores de cadeia de caracteres.  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 Como alternativa, você pode obter o mesmo resultado usando o código a seguir:  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 Cada essas declarações é equivalente ao exemplo a seguir, que cria um `Customer` objeto usando o construtor padrão e, em seguida, especifica os valores iniciais para o `Name` e `City` propriedades usando um `With` instrução.  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 Se o `Customer` classe contém um construtor com parâmetros que permite enviar um valor para `Name`, por exemplo, você pode também declarar e inicializar uma `Customer` objeto das seguintes maneiras:  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 Você não precisa inicializar todas as propriedades, como mostra o código a seguir.  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 No entanto, a lista de inicialização não pode estar vazia. Propriedades não inicializadas mantém seus valores padrão.  
  
### <a name="type-inference-with-named-types"></a>Inferência de tipo com tipos nomeados  
 Você pode encurtar o código para a declaração de `cust1` combinando inicializadores de objeto e Inferência de tipo local. Isso permite que você omitir o `As` cláusula na declaração da variável. O tipo de dados da variável é deduzido do tipo de objeto que é criado pela atribuição. No exemplo a seguir, o tipo de `cust6` é `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>Comentários sobre tipos nomeados  
  
-   Um membro de classe não pode ser inicializado mais de uma vez na lista de inicializador de objeto. A declaração de `cust7` causa um erro.  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   Um membro pode ser usado para inicializar a mesmo ou outro campo. Se um membro é acessado antes de ele ter sido inicializado, como a declaração a seguir para `cust8`, o valor padrão será usado. Lembre-se de que, quando uma declaração que usa um inicializador de objeto é processada, a primeira coisa que acontece é que o construtor apropriado é chamado. Depois disso, os campos individuais na lista de inicializador são inicializados. Nos exemplos a seguir, o valor padrão para `Name` é atribuído para `cust8`, e é atribuído um valor inicializado `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     O exemplo a seguir usa o construtor com parâmetros de `cust3` e `cust4` declarar e inicializar `cust10` e `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   Inicializadores de objeto podem ser aninhados. No exemplo a seguir, `AddressClass` é uma classe que tem duas propriedades, `City` e `State`e o `Customer` classe tiver um `Address` propriedade que é uma instância de `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   A lista de inicialização não pode estar vazia.  
  
-   A instância que está sendo inicializada não pode ser do tipo de objeto.  
  
-   Membros de classe que está sendo inicializados não podem ser membros compartilhados, membros somente leitura, constantes ou chamadas de método.  
  
-   Membros de classe que está sendo inicializados não podem ser indexados ou qualificados. Os exemplos a seguir geram erros de compilador:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Tipos anônimos  
 Tipos anônimos usam inicializadores de objeto para criar instâncias dos novos tipos de que você não definir explicitamente e nome. Em vez disso, o compilador gera um tipo de acordo com as propriedades que você designar na lista de inicializador de objeto. Porque o nome do tipo não for especificado, ele é chamado como uma *tipo anônimo*. Por exemplo, comparar a declaração a seguir para o anterior para `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 Sintaticamente, a única diferença é que nenhum nome for especificado após `New` para o tipo de dados. No entanto, o que acontece é bastante diferente. O compilador define um novo tipo anônimo que tem duas propriedades, `Name` e `City`e cria uma instância dele com os valores especificados. Inferência de tipo determina os tipos de `Name` e `City` no exemplo para ser cadeias de caracteres.  
  
> [!CAUTION]
>  O nome do tipo anônimo é gerado pelo compilador e pode variar de compilação a compilação. O código não deve usar ou contar com o nome de um tipo anônimo.  
  
 Como o nome do tipo não estiver disponível, você não pode usar um `As` cláusula declarar `cust13`. O tipo deve ser inferido. Sem o uso de associação tardia, isso limita o uso dos tipos anônimos para variáveis locais.  
  
 Tipos anônimos oferecem suporte crítico para [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consultas. Para obter mais informações sobre o uso de tipos anônimos em consultas, consulte [tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) e [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Comentários sobre tipos anônimos  
  
-   Normalmente, todos ou a maioria das propriedades em uma declaração de tipo anônimo será propriedades de chave, que são indicadas digitando a palavra-chave `Key` na frente do nome de propriedade.  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     Para obter mais informações sobre propriedades de chave, consulte [chave](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   Chamado como tipos de listas de inicializadores para definições de tipo anônimo devem declarar pelo menos uma propriedade.  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   Quando uma instância de um tipo anônimo for declarada, o compilador gera uma definição de tipo anônimo correspondente. Os nomes e tipos de dados das propriedades são tirados a declaração da instância e são incluídos pelo compilador na definição do. As propriedades não são nomeadas e definidas com antecedência, como no caso de um tipo nomeado. Os tipos são inferidos. Você não pode especificar os tipos de dados das propriedades usando um `As` cláusula.  
  
-   Tipos anônimos também podem estabelecer os nomes e valores de suas propriedades de várias outras maneiras. Por exemplo, uma propriedade de tipo anônimo pode levar o nome e o valor de uma variável, ou o nome e valor de uma propriedade de outro objeto.  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     Para obter mais informações sobre as opções para definir propriedades em tipos anônimos, consulte [como: inferir nomes de propriedade e tipos de declarações de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Consulte também  
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Chave](../../../../visual-basic/language-reference/modifiers/key.md)  
 [Como declarar um objeto usando um inicializador de objeto](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
