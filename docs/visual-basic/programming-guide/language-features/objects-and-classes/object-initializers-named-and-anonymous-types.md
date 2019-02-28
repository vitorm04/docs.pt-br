---
title: 'Inicializadores de objeto: Tipos nomeados e anônimos (Visual Basic)'
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
ms.openlocfilehash: d4f82cab8bcdeb3e0553649f8a569ae24bafc707
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974348"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Inicializadores de objeto: Tipos nomeados e anônimos (Visual Basic)
Inicializadores de objeto permitem que você especifique propriedades para um objeto complexo usando uma única expressão. Eles podem ser usados para criar instâncias de tipos nomeados e de tipos anônimos.  
  
## <a name="declarations"></a>Declarations  
 Declarações de instâncias de tipos nomeados e anônimos podem parecer quase idênticas, mas seus efeitos não são iguais. Cada categoria tem capacidades e as restrições de seu próprio. O exemplo a seguir mostra uma maneira conveniente de declarar e inicializar uma instância de uma classe nomeada, `Customer`, usando uma lista de inicializadores de objeto. Observe que o nome da classe é especificado após a palavra-chave `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 Um tipo anônimo tem nenhum nome utilizável. Portanto, uma instanciação de um tipo anônimo não pode incluir um nome de classe.  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 Os requisitos e os resultados de duas declarações não são os mesmos. Para `namedCust`, um `Customer` classe que tem um `Name` propriedade já deve existir e a declaração cria uma instância dessa classe. Para `anonymousCust`, o compilador define uma nova classe que tem uma propriedade, uma cadeia de caracteres chamada `Name`e cria uma nova instância dessa classe.  
  
## <a name="named-types"></a>Tipos nomeados  
 Inicializadores de objeto fornecem uma maneira simple para chamar o construtor de um tipo e, em seguida, defina os valores de algumas ou todas as propriedades em uma única instrução. O compilador invoca o construtor apropriado para a instrução: o construtor padrão se nenhum argumento é apresentado ou um construtor com parâmetros, se um ou mais argumentos são enviados. Depois disso, as propriedades especificadas são inicializadas na ordem em que são apresentados na lista de inicializadores.  
  
 Consiste em cada inicialização na lista de inicializadores a atribuição de um valor inicial a um membro da classe. Os nomes e tipos de dados dos membros são determinados quando a classe é definida. Nos exemplos a seguir, o `Customer` classe deve existir e devem ter membros nomeado `Name` e `City` que pode aceitar valores de cadeia de caracteres.  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 Como alternativa, você pode obter o mesmo resultado usando o código a seguir:  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 Cada uma dessas declarações é equivalente ao exemplo a seguir, que cria um `Customer` usando o construtor padrão de objeto e, em seguida, especifica os valores iniciais para o `Name` e `City` propriedades usando um `With` instrução.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 Se o `Customer` classe contém um construtor com parâmetros que permite que você envie um valor para `Name`, por exemplo, você pode também declarar e inicializar uma `Customer` objeto das seguintes maneiras:  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 Não é preciso inicializar todas as propriedades, como mostra o código a seguir.  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 No entanto, a lista de inicialização não pode estar vazia. Propriedades não inicializadas retêm seus valores padrão.  
  
### <a name="type-inference-with-named-types"></a>Inferência de tipos com tipos nomeados  
 Você pode reduzir o código para a declaração de `cust1` , combinando os inicializadores de objeto e Inferência de tipo local. Isso permite que você omita a `As` cláusula na declaração da variável. O tipo de dados da variável é inferido do tipo do objeto que é criado pela atribuição. No exemplo a seguir, o tipo de `cust6` é `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>Comentários sobre os tipos nomeados  
  
-   Um membro de classe não pode ser inicializado mais de uma vez na lista de inicializadores de objeto. A declaração de `cust7` causa um erro.  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
-   Um membro pode ser usado para inicializar a mesmo ou outro campo. Se um membro é acessado antes de ele ter sido inicializado, como a seguinte declaração para `cust8`, o valor padrão será usado. Lembre-se de que, quando uma declaração que usa um inicializador de objeto é processada, a primeira coisa que acontece é que o construtor apropriado é invocado. Depois disso, os campos individuais na lista de inicializadores são inicializados. Nos exemplos a seguir, o valor padrão para `Name` atribuída `cust8`, e é atribuído um valor inicializado `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     O exemplo a seguir usa o construtor com parâmetros de `cust3` e `cust4` declarar e inicializar `cust10` e `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
-   Inicializadores de objeto podem ser aninhados. No exemplo a seguir `AddressClass` é uma classe que tem duas propriedades, `City` e `State`e o `Customer` classe tem um `Address` propriedade que é uma instância de `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
-   A lista de inicialização não pode estar vazia.  
  
-   A instância que está sendo inicializada não pode ser do tipo de objeto.  
  
-   Membros de classe que está sendo inicializados não podem ser membros compartilhados, membros somente leitura, constantes ou chamadas de método.  
  
-   Membros de classe que está sendo inicializados não podem ser indexados ou qualificados. Os exemplos a seguir geram erros de compilador:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Tipos anônimos  
 Tipos anônimos usam inicializadores de objeto para criar instâncias dos novos tipos que você não define explicitamente e nome. Em vez disso, o compilador gera um tipo de acordo com as propriedades que você designar na lista de inicializadores de objeto. Porque o nome do tipo não for especificado, ele é considerado um *tipo anônimo*. Por exemplo, comparar a declaração a seguir com a de antes para `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 Sintaticamente, a única diferença é que nenhum nome for especificado após `New` para o tipo de dados. No entanto, o que acontece é bastante diferente. O compilador define um novo tipo anônimo que tem duas propriedades, `Name` e `City`e cria uma instância com os valores especificados. Inferência de tipo determina os tipos de `Name` e `City` no exemplo para ser cadeias de caracteres.  
  
> [!CAUTION]
>  O nome do tipo anônimo é gerado pelo compilador e pode variar de compilação a compilação. Seu código não deve usar ou contar com o nome de um tipo anônimo.  
  
 Como o nome do tipo não estiver disponível, você não pode usar um `As` cláusula declarar `cust13`. Seu tipo deve ser inferido. Sem o uso de associação tardia, isso limita o uso de tipos anônimos para variáveis locais.  
  
 Os tipos anônimos fornecem suporte crítico para [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consultas. Para obter mais informações sobre o uso de tipos anônimos em consultas, consulte [tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) e [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Comentários sobre tipos anônimos  
  
-   Normalmente, todos ou a maioria das propriedades em uma declaração de tipo anônimo será propriedades de chave, que são indicadas, digitando a palavra-chave `Key` na frente do nome de propriedade.  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     Para obter mais informações sobre propriedades de chave, consulte [chave](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   Chamado como tipos de listas de inicializadores para definições de tipo anônimo devem declarar pelo menos uma propriedade.  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
-   Quando uma instância de um tipo anônimo é declarada, o compilador gera uma definição de tipo anônimo correspondente. Os nomes e tipos de dados das propriedades são obtidos da declaração de instância e são incluídos pelo compilador na definição. As propriedades não são nomeadas e definidas com antecedência, como seriam para um tipo nomeado. Os tipos são inferidos. Você não pode especificar os tipos de dados das propriedades usando um `As` cláusula.  
  
-   Tipos anônimos também podem estabelecer os nomes e valores de suas propriedades de várias outras maneiras. Por exemplo, uma propriedade de tipo anônimo pode levar o nome e o valor de uma variável, ou o nome e valor de uma propriedade de outro objeto.  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     Para obter mais informações sobre as opções para definir propriedades em tipos anônimos, consulte [como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Consulte também
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Chave](../../../../visual-basic/language-reference/modifiers/key.md)
- [Como: Declarar um objeto usando um inicializador de objeto](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
