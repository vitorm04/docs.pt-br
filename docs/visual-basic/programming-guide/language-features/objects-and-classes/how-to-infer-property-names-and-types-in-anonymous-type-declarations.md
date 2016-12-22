---
title: "Como inferir nomes e tipos de propriedade em declara&#231;&#245;es de tipo an&#244;nimo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "inferindo nomes de propriedade [Visual Basic]"
  - "tipos anônimos [Visual Basic] inferindo tipos e nomes de propriedade"
  - "inferindo tipos de propriedade [Visual Basic]"
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como inferir nomes e tipos de propriedade em declara&#231;&#245;es de tipo an&#244;nimo (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Tipos anônimos fornecem nenhum mecanismo para especificar os tipos de dados de propriedades diretamente. Tipos de todas as propriedades são inferidos. No exemplo a seguir, os tipos de `Name` e `Price` são inferidos diretamente dos valores que são usados para inicializá\-los.  
  
 [!CODE [VbVbalrAnonymousTypes#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#1)]  
  
 Tipos anônimos também podem interpretar nomes de propriedade e tipos de outras fontes. As seções a seguir fornecem uma lista de circunstâncias onde a inferência é possível e exemplos de situações onde não é.  
  
## Inferência bem\-sucedida  
  
#### Tipos anônimos podem inferir nomes de propriedade e tipos das seguintes fontes:  
  
-   Dos nomes de variável. Tipo anônimo `anonProduct` terá duas propriedades, `productName` e `productPrice`. Os tipos de dados será das variáveis originais, `String` e `Double`, respectivamente.  
  
     [!CODE [VbVbalrAnonymousTypes#11](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#11)]  
  
-   De propriedade ou campo nomes de outros objetos. Por exemplo, considere uma `car` objeto de um `CarClass` tipo que inclui `Name` e `ID` Propriedades. Para criar uma nova instância de tipo anônimo, `car1`, com `Name` e `ID` propriedades que são inicializadas com os valores da `car` do objeto, você pode escrever o seguinte:  
  
     [!CODE [VbVbalrAnonymousTypes#34](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#34)]  
  
     A declaração anterior é equivalente a mais a linha de código que define o tipo anônimo `car2`.  
  
     [!CODE [VbVbalrAnonymousTypes#35](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#35)]  
  
-   De XML membro nomes.  
  
     [!CODE [VbVbalrAnonymousTypes#12](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#12)]  
  
     O tipo resultante para `anon` teria uma propriedade, `Book`, do tipo <xref:System.Collections.IEnumerable>\(de XElement\).  
  
-   De uma função que não tem parâmetros, como `SomeFunction` no exemplo a seguir.  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     A variável `anon2` no código a seguir é um tipo anônimo que tem uma propriedade, um caractere chamado `First`. Esse código irá exibir uma letra "E", a letra que é retornada pela função <xref:System.Linq.Enumerable.First%2A>.  
  
     [!CODE [VbVbalrAnonymousTypes#13](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#13)]  
  
## A inferência de falhas  
  
#### Nome inferência falhará em muitas circunstâncias, incluindo o seguinte:  
  
-   A inferência deriva de invocação de um método, um construtor ou uma propriedade parametrizada que requer argumentos. A declaração anterior de `anon1` falhará se `someFunction` possui um ou mais argumentos.  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     Atribuição a um novo nome de propriedade resolve o problema.  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   A inferência deriva de uma expressão complexa.  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     O erro pode ser resolvido atribuindo o resultado da expressão a um nome de propriedade.  
  
     [!CODE [VbVbalrAnonymousTypes#14](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#14)]  
  
-   Inferência de várias propriedades produz dois ou mais propriedades que têm o mesmo nome. Referência de volta a declarações nos exemplos anteriores, você não pode listar os dois `product.Name` e `car1.Name` como propriedades do mesmo tipo anônimo. Isso ocorre porque o identificador inferido para cada um deles seria `Name`.  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     O problema pode ser resolvido atribuindo valores a nomes de propriedades distintas.  
  
     [!CODE [VbVbalrAnonymousTypes#36](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#36)]  
  
     Observe que as alterações caso \(alterações entre letras maiúsculas e minúsculas\) não faça dois nomes distintos.  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   O tipo inicial e o valor de uma propriedade depende outra propriedade que ainda não foi estabelecida. Por exemplo, `.IDName = .LastName` não é válido em uma declaração de tipo anônimo, a menos que `.LastName` já foi inicializado.  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     Neste exemplo, você pode corrigir o problema, invertendo a ordem na qual as propriedades são declaradas.  
  
     [!CODE [VbVbalrAnonymousTypes#15](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#15)]  
  
-   Um nome de propriedade do tipo anônimo é o mesmo que o nome de um membro do <xref:System.Object>. Por exemplo, a seguinte declaração falha porque `Equals` é um método de <xref:System.Object>.  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     Você pode corrigir o problema alterando o nome da propriedade:  
  
     [!CODE [VbVbalrAnonymousTypes#16](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#16)]  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Chave](../../../../visual-basic/language-reference/modifiers/key.md)