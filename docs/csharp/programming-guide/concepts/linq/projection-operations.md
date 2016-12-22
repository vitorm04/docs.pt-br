---
title: "Opera&#231;&#245;es de proje&#231;&#227;o (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Opera&#231;&#245;es de proje&#231;&#227;o (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Projeção refere\-se a operação de transformar um objeto em um novo formulário que geralmente consiste apenas as propriedades que serão usadas posteriormente. Usando a projeção, você pode criar um novo tipo que é criado a partir de cada objeto. Você pode projetar uma propriedade e executar uma função matemática nele. Você também pode projetar o objeto original sem alterá\-lo.  
  
 Os métodos de operador de consulta padrão que executam projeção são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta c\#|Mais Informações|  
|--------------------|---------------|------------------------------------------|----------------------|  
|Selecione|Valores de projetos com base em uma função de transformação.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=fullName>|  
|SelectMany|Sequências de projetos de valores que se baseiam em uma função de transformação e, em seguida, nivela\-los em uma sequência.|Usar várias `from` cláusulas|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName>|  
  
## Exemplos de sintaxe de expressão de consulta  
  
### Selecione  
 O exemplo a seguir usa o `select` cláusula para projetar a primeira letra de cada cadeia de caracteres em uma lista de cadeias de caracteres.  
  
```c#  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### SelectMany  
 O exemplo a seguir usa vários `from` cláusulas para cada palavra de cada cadeia de caracteres em uma lista de cadeias de caracteres de projeto.  
  
```c#  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## Selecione versus SelectMany  
 O trabalho de ambos `Select()` e `SelectMany()` é produzir um resultado \(ou valores\) de valores de origem.`Select()` produz um valor de resultado para cada valor de origem. O resultado geral, portanto, é uma coleção que tem o mesmo número de elementos que a coleção de origem. Por outro lado, `SelectMany()` produz um único resultado geral que contém subcoleções concatenadas de cada valor de origem. A função de transformação que é passada como um argumento para `SelectMany()` deve retornar uma seqüência enumerável de valores para cada valor de origem. Essas sequências enumeráveis depois são concatenadas por `SelectMany()` para criar uma sequência grande.  
  
 As ilustrações a seguir mostram a diferença conceitual entre as ações desses dois métodos. Em cada caso, suponha que a função de seletor \(transformação\) seleciona a matriz de flores de cada valor de origem.  
  
 Esta ilustração mostra como `Select()` retorna uma coleção que tem o mesmo número de elementos como a coleção de origem.  
  
 ![Ilustração conceitual da ação de Select&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Esta ilustração mostra como `SelectMany()` concatena a sequência intermediária de matrizes em um valor de resultado final que contém cada valor de cada matriz intermediário.  
  
 ![Gráfico mostrando a ação de SelectMany &#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### Exemplo de código  
 O exemplo a seguir compara o comportamento de `Select()` e `SelectMany()`. O código cria um "Buquê" de flores executando os primeiros dois itens de cada lista de nomes da flor na coleção de origem. Neste exemplo, o "valor único" que a função de transformação <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> usa é uma coleção de valores. Isso requer o extra `foreach` loop para enumerar cada cadeia de caracteres em cada sequência subpropriedades.  
  
```c#  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********              
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula select](../../../../csharp/language-reference/keywords/select-clause.md)   
 [Como: preencher coleções de objetos de várias fontes \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)   
 [Como: dividir um arquivo em vários arquivos usando grupos \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)