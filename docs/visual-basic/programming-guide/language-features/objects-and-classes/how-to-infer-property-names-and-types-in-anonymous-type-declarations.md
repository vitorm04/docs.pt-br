---
title: 'Como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 67cc9e85d249365a7b4b7636c99766087314622d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596847"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo (Visual Basic)
Tipos anônimos não fornecem um mecanismo para especificar diretamente os tipos de dados de propriedades. Tipos de todas as propriedades são inferidos. No exemplo a seguir, os tipos de `Name` e `Price` são inferidos diretamente dos valores que são usados para inicializá-los.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 Tipos anônimos também podem interpretar os nomes de propriedade e tipos de outras fontes. As seções a seguir fornecem uma lista de circunstâncias em que a inferência de tipos é possível e exemplos de situações em que não é.  
  
## <a name="successful-inference"></a>Inferência bem-sucedida  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Tipos anônimos podem inferir nomes de propriedade e tipos das seguintes fontes:  
  
-   De nomes de variáveis. Tipo anônimo `anonProduct` terá duas propriedades, `productName` e `productPrice`. Os tipos de dados será das variáveis do originais `String` e `Double`, respectivamente.  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   De nomes de campo ou propriedade de outros objetos. Por exemplo, considere uma `car` objeto de um `CarClass` tipo que inclui `Name` e `ID` propriedades. Para criar uma nova instância de tipo anônimo, `car1`, com `Name` e `ID` propriedades que são inicializadas com os valores do `car` do objeto, você pode escrever o seguinte:  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     A declaração anterior é equivalente a mais a linha de código que define o tipo anônimo `car2`.  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   De nomes de membro XML.  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     O tipo resultante para `anon` teria uma propriedade, `Book`, do tipo <xref:System.Collections.IEnumerable>(de XElement).  
  
-   De uma função que não tem parâmetros, como `SomeFunction` no exemplo a seguir.  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     A variável `anon2` no código a seguir é um tipo anônimo que tem uma propriedade, um caractere chamado `First`. Esse código exibirá uma letra "E", a letra que é retornada pela função <xref:System.Linq.Enumerable.First%2A>.  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a>A inferência de falhas  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>A inferência de nome falhará em muitas circunstâncias, incluindo o seguinte:  
  
-   A inferência deriva de invocação de um método, um construtor ou uma propriedade com parâmetros que requer argumentos. A declaração anterior de `anon1` falhará se `someFunction` tem um ou mais argumentos.  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     Atribuição para um novo nome de propriedade resolve o problema.  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   A inferência deriva de uma expressão complexa.  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     O erro pode ser resolvido ao atribuir o resultado da expressão a um nome de propriedade.  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   Inferência de várias propriedades produz dois ou mais propriedades que têm o mesmo nome. Referência de volta às declarações nos exemplos anteriores, você não pode listar os dois `product.Name` e `car1.Name` como propriedades do mesmo tipo anônimo. Isso ocorre porque o identificador inferido para cada um deles seria `Name`.  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     O problema pode ser resolvido por meio da atribuição de valores para nomes de propriedade distintos.  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     Observe que alterações caso (alterações entre letras maiusculas e minúsculas) não faça dois nomes distintos.  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   O tipo inicial e o valor de uma propriedade depende de outra propriedade que ainda não foi estabelecida. Por exemplo, `.IDName = .LastName` não é válido em uma declaração de tipo anônimo, a menos que `.LastName` já foi inicializado.  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     Neste exemplo, você pode corrigir o problema, invertendo a ordem na qual as propriedades são declaradas.  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   Um nome de propriedade do tipo anônimo é igual ao nome de um membro de <xref:System.Object>. Por exemplo, a seguinte declaração falhará porque `Equals` é um método de <xref:System.Object>.  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     Você pode corrigir o problema, alterando o nome da propriedade:  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Inicializadores de objeto: Tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Chave](../../../../visual-basic/language-reference/modifiers/key.md)
