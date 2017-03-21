---
title: "Inicializadores de objeto: Tipos nomeados e anônimos (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ObjectInitializer
dev_langs:
- VB
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d684ad4f3dd47dc7400ea401a94660af832ef866
ms.lasthandoff: 03/13/2017

---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Inicializadores de objeto: tipos nomeados e anônimos (Visual Basic)
Inicializadores de objeto permitem especificar propriedades para um objeto complexo usando uma única expressão. Eles podem ser usados para criar instâncias dos tipos nomeados e de tipos anônimos.  
  
## <a name="declarations"></a>Declarações  
 Declarações de instâncias de tipos nomeados e anônimos podem parecer quase idênticas, mas seus efeitos não são iguais. Cada categoria tem capacidades e restrições de seu próprio. O exemplo a seguir mostra uma maneira conveniente de declarar e inicializar uma instância de uma classe nomeada, `Customer`, usando uma lista de inicializadores de objeto. Observe que o nome da classe é especificado após a palavra-chave `New`.  
  
 [!code-vb[VbVbalrObjectInit n º&1;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 Um tipo anônimo não tem nenhum nome utilizável. Portanto, uma instanciação de um tipo anônimo não pode incluir um nome de classe.  
  
 [!code-vb[VbVbalrObjectInit n º&2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 Os requisitos e os resultados de duas declarações não são os mesmos. Para `namedCust`, um `Customer` classe que tem um `Name` propriedade já deve existir e a declaração cria uma instância dessa classe. Para `anonymousCust`, o compilador define uma nova classe que tem uma propriedade, uma cadeia de caracteres chamada `Name`e cria uma nova instância da classe.  
  
## <a name="named-types"></a>Tipos nomeados  
 Inicializadores de objeto fornecem uma maneira simples para chamar o construtor de um tipo e, em seguida, defina os valores de algumas ou todas as propriedades em uma única instrução. O compilador chama o construtor apropriado para a instrução: o construtor padrão se nenhum argumento é apresentado ou um construtor com parâmetros, se um ou mais argumentos são enviados. Depois disso, as propriedades especificadas são inicializadas na ordem em que são apresentados na lista de inicializadores.  
  
 Consiste em cada inicialização na lista de inicializadores a atribuição de um valor inicial para um membro da classe. Os nomes e tipos de dados dos membros são determinados quando a classe é definida. Nos exemplos a seguir, o `Customer` classe deve existir e devem ter membros nomeada `Name` e `City` que pode aceitar valores de cadeia de caracteres.  
  
 [!code-vb[VbVbalrObjectInit n º&3;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 Como alternativa, você pode obter o mesmo resultado usando o código a seguir:  
  
 [!code-vb[VbVbalrObjectInit n º&4;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 Cada uma dessas declarações é equivalente ao exemplo a seguir, que cria um `Customer` de objeto usando o construtor padrão e, em seguida, especifica valores iniciais para o `Name` e `City` propriedades usando um `With` instrução.  
  
 [!code-vb[VbVbalrObjectInit n º&5;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 Se o `Customer` classe contém um construtor com parâmetros que permite que você envie um valor para `Name`, por exemplo, você também pode declarar e inicializar uma `Customer` objeto das seguintes maneiras:  
  
 [!code-vb[VbVbalrObjectInit n º&6;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 Você não precisa inicializar todas as propriedades, como mostra o código a seguir.  
  
 [!code-vb[VbVbalrObjectInit&#7;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 No entanto, a lista de inicialização não pode ficar vazia. Propriedades não inicializadas retêm seus valores padrão.  
  
### <a name="type-inference-with-named-types"></a>Inferência de tipos com tipos nomeados  
 Você pode reduzir o código para a declaração de `cust1` , combinando os inicializadores de objeto e Inferência de tipo local. Isso permite que você omita o `As` cláusula na declaração da variável. O tipo de dados da variável é inferido do tipo de objeto que é criado pela atribuição. No exemplo a seguir, o tipo de `cust6` é `Customer`.  
  
 [!code-vb[VbVbalrObjectInit n º&8;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>Comentários sobre tipos nomeados  
  
-   Um membro de classe não pode ser inicializado mais de uma vez na lista de inicializadores de objeto. A declaração de `cust7` causa um erro.  
  
     [!code-vb[VbVbalrObjectInit n º&9;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   Um membro pode ser usado para inicializar a mesmo ou outro campo. Se um membro é acessado antes de ele ter sido inicializado, como a declaração a seguir para `cust8`, o valor padrão será usado. Lembre-se de que, quando uma declaração que usa um inicializador de objeto é processada, a primeira coisa que acontece é que o construtor apropriado é invocado. Depois disso, os campos individuais na lista de inicializadores são inicializados. Nos exemplos a seguir, o valor padrão para `Name` é atribuído para `cust8`, e é atribuído um valor inicializado `cust9`.  
  
     [!code-vb[VbVbalrObjectInit n º&10;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     O exemplo a seguir usa o construtor com parâmetros de `cust3` e `cust4` para declarar e inicializar `cust10` e `cust11`.  
  
     [!code-vb[VbVbalrObjectInit n º&11;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   Inicializadores de objeto podem ser aninhados. No exemplo a seguir, `AddressClass` é uma classe que tem duas propriedades, `City` e `State`e o `Customer` classe tem um `Address` propriedade que é uma instância de `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit&#12;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   A lista de inicialização não pode ficar vazia.  
  
-   A instância que está sendo inicializada não pode ser do tipo de objeto.  
  
-   Membros de classe que está sendo inicializados não podem ser membros somente leitura, membros compartilhados, constantes ou chamadas de método.  
  
-   Membros de classe que está sendo inicializados não podem ser indexados ou qualificados. Os exemplos a seguir geram erros de compilador:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Tipos anônimos  
 Tipos anônimos usam inicializadores de objeto para criar instâncias dos novos tipos de que você não definir explicitamente e nome. Em vez disso, o compilador gera um tipo de acordo com as propriedades que você designa na lista de inicializadores de objeto. Porque o nome do tipo não for especificado, ele é considerado um *tipo anônimo*. Por exemplo, comparar a seguinte declaração à anteriores para `cust6`.  
  
 [!code-vb[VbVbalrObjectInit&13;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 Sintaticamente, a única diferença é que nenhum nome for especificado após `New` para o tipo de dados. No entanto, o que acontece é bastante diferente. O compilador define um novo tipo anônimo com duas propriedades, `Name` e `City`e cria uma instância com os valores especificados. Inferência de tipo determina os tipos de `Name` e `City` no exemplo para ser cadeias de caracteres.  
  
> [!CAUTION]
>  O nome do tipo anônimo é gerado pelo compilador e pode variar de compilação a compilação. Seu código não deve usar ou contar com o nome de um tipo anônimo.  
  
 Como o nome do tipo não estiver disponível, você não pode usar um `As` cláusula declarar `cust13`. Seu tipo deve ser inferido. Sem o uso de associação tardia, isso limita o uso dos tipos anônimos para variáveis locais.  
  
 Tipos anônimos fornecem suporte crítico para [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas. Para obter mais informações sobre o uso de tipos anônimos em consultas, consulte [tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) e [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Comentários sobre tipos anônimos  
  
-   Normalmente, todas ou a maioria das propriedades em uma declaração de tipo anônimo será propriedades de chave, que são indicadas, digitando a palavra-chave `Key` na frente do nome da propriedade.  
  
     [!code-vb[VbVbalrObjectInit&#14;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     Para obter mais informações sobre propriedades de chave, consulte [chave](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   Nomeado como tipos de listas de inicializadores para definições de tipo anônimo devem declarar pelo menos uma propriedade.  
  
     [!code-vb[VbVbalrObjectInit n º&2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   Quando uma instância de um tipo anônimo é declarada, o compilador gera uma definição de tipo anônimo correspondente. Os nomes e tipos de dados das propriedades ficam da declaração de instância e são incluídos pelo compilador na definição. As propriedades não são chamadas e definidas com antecedência, como seriam um tipo nomeado. Os tipos são inferidos. Você não pode especificar os tipos de dados das propriedades usando um `As` cláusula.  
  
-   Tipos anônimos também podem estabelecer os nomes e valores de suas propriedades de várias outras maneiras. Por exemplo, uma propriedade de tipo anônimo pode levar o nome e o valor de uma variável, ou o nome e valor de uma propriedade de outro objeto.  
  
     [!code-vb[VbVbalrObjectInit&#15;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     Para obter mais informações sobre as opções para definir propriedades em tipos anônimos, consulte [como: inferir nomes de propriedade e tipos nas declarações de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Consulte também  
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Como: inferir nomes de propriedade e tipos nas declarações de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Chave](../../../../visual-basic/language-reference/modifiers/key.md)   
 [Como declarar um objeto usando um inicializador de objeto](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
