---
title: "Opera&#231;&#245;es de proje&#231;&#227;o (Visual Basic) | Microsoft Docs"
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
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Opera&#231;&#245;es de proje&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Projeção refere\-se a operação de transformar um objeto em um novo formulário que geralmente consiste apenas as propriedades que serão usadas posteriormente. Usando a projeção, você pode criar um novo tipo que é criado a partir de cada objeto. Você pode projetar uma propriedade e executar uma função matemática nele. Você também pode projetar o objeto original sem alterá\-lo.  
  
 Os métodos de operador de consulta padrão que executam projeção são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais Informações|  
|--------------------|---------------|------------------------------------------------------|----------------------|  
|Selecione|Valores de projetos com base em uma função de transformação.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=fullName>|  
|SelectMany|Sequências de projetos de valores que se baseiam em uma função de transformação e, em seguida, nivela\-los em uma sequência.|Usar várias `From` cláusulas|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName>|  
  
## Exemplos de sintaxe de expressão de consulta  
  
### Selecione  
 O exemplo a seguir usa o `Select` cláusula para projetar a primeira letra de cada cadeia de caracteres em uma lista de cadeias de caracteres.  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### SelectMany  
 O exemplo a seguir usa vários `From` cláusulas para cada palavra de cada cadeia de caracteres em uma lista de cadeias de caracteres de projeto.  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## Selecione versus SelectMany  
 O trabalho de ambos `Select()` e `SelectMany()` é produzir um resultado \(ou valores\) de valores de origem.`Select()` produz um valor de resultado para cada valor de origem. O resultado geral, portanto, é uma coleção que tem o mesmo número de elementos que a coleção de origem. Por outro lado, `SelectMany()` produz um único resultado geral que contém subcoleções concatenadas de cada valor de origem. A função de transformação que é passada como um argumento para `SelectMany()` deve retornar uma seqüência enumerável de valores para cada valor de origem. Essas sequências enumeráveis depois são concatenadas por `SelectMany()` para criar uma sequência grande.  
  
 As ilustrações a seguir mostram a diferença conceitual entre as ações desses dois métodos. Em cada caso, suponha que a função de seletor \(transformação\) seleciona a matriz de flores de cada valor de origem.  
  
 Esta ilustração mostra como `Select()` retorna uma coleção que tem o mesmo número de elementos como a coleção de origem.  
  
 ![Ilustração conceitual da ação de Select&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Esta ilustração mostra como `SelectMany()` concatena a sequência intermediária de matrizes em um valor de resultado final que contém cada valor de cada matriz intermediário.  
  
 ![Gráfico mostrando a ação de SelectMany &#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### Exemplo de código  
 O exemplo a seguir compara o comportamento de `Select()` e `SelectMany()`. O código cria um "Buquê" de flores executando os primeiros dois itens de cada lista de nomes da flor na coleção de origem. Neste exemplo, o "valor único" que a função de transformação <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> usa é uma coleção de valores. Isso requer o extra `For Each` loop para enumerar cada cadeia de caracteres em cada sequência subpropriedades.  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md)   
 [Como combinar dados com junções](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Como: preencher coleções de objetos de várias fontes \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)   
 [Como retornar um resultado de consulta LINQ como um tipo específico](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)   
 [Como: dividir um arquivo em vários arquivos usando grupos \(LINQ\) \(Visual Basic\)](../Topic/How%20to:%20Split%20a%20File%20Into%20Many%20Files%20by%20Using%20Groups%20\(LINQ\)%20\(Visual%20Basic\).md)