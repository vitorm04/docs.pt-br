---
title: Inicializadores de objeto e coleção – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 60c4e8c5b83ee1c279bf8e7f4905ef9f2cf814b4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243160"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicializadores de objeto e coleção (Guia de Programação em C#)
Os inicializadores de objeto permitem atribuir valores a quaisquer campos ou propriedades acessíveis de um objeto na hora de criação sem que seja necessário invocar um construtor seguido por linhas de instruções de atribuição. A sintaxe do inicializador de objeto permite especificar argumentos para um construtor ou omitir os argumentos (e a sintaxe de parênteses).  O exemplo a seguir mostra como usar um inicializador de objeto com um tipo nomeado `Cat` e como invocar o construtor padrão. Observe o uso de propriedades autoimplementadas na classe `Cat`. Para obter mais informações, consulte [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
A sintaxe dos inicializadores de objetos permite que você crie uma instância, e depois atribui o objeto recém-criado, com suas propriedades atribuídas, à variável na atribuição.
  
## <a name="object-initializers-with-anonymous-types"></a>Inicializadores de objeto com tipos anônimos  
 Embora inicializadores de objetos possam ser usados em qualquer contexto, eles são especialmente úteis em expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Expressões de consulta fazem uso frequente de [tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), que podem ser inicializados somente usando um inicializador de objeto, como mostrado na declaração a seguir.  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 Os tipos anônimos habilitam a cláusula `select` em uma expressão de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a transformar objetos da sequência original em objetos cujo valor e forma podem diferir dos originais. Isso será útil se você desejar armazenar apenas uma parte das informações de cada objeto em uma sequência. No exemplo a seguir, suponha que um objeto de produto (`p`) contenha vários campos e métodos e que você esteja apenas interessado em criar uma sequência de objetos que contenha o nome do produto e o preço unitário.  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 Quando essa consulta for executada, a variável `productInfos` conterá uma sequência de objetos que podem ser acessados em uma instrução `foreach` como mostrado neste exemplo:  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 Cada objeto no novo tipo anônimo tem duas propriedades públicas que recebem os mesmos nomes que as propriedades ou os campos no objeto original. Você também poderá renomear um campo quando estiver criando um tipo anônimo; o exemplo a seguir renomeia o campo `UnitPrice` como `Price`.  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="collection-initializers"></a>Inicializadores de coleção  
 Os inicializadores de coleção permitem especificar um ou mais inicializadores de elemento quando você inicializa um tipo de coleção que implementa <xref:System.Collections.IEnumerable> e tem `Add` com a assinatura apropriada como um método de instância ou um método de extensão. Os inicializadores de elemento podem ser um valor simples, uma expressão ou um inicializador de objeto. Ao usar um inicializador de coleção, não é necessário especificar várias chamadas para o método `Add` da classe em seu código-fonte; o compilador adiciona as chamadas.  
  
 Os exemplos a seguir mostram dois inicializadores de coleção simples:  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 O inicializador de coleção a seguir usa inicializadores de objeto para inicializar objetos da classe `Cat` definida em um exemplo anterior. Observe que os inicializadores de objeto individuais são envolvidos por chaves e separados por vírgulas.  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 Você poderá especificar [nulo](../../../csharp/language-reference/keywords/null.md) como um elemento em um inicializador de coleção se o método `Add` da coleção permitir.  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 É possível especificar elementos indexados se a coleção der suporte a indexação.  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a>Exemplos

 O exemplo a seguir combina os conceitos de inicializadores de coleção e objeto.

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 Mostrado no exemplo a seguir, um objeto que implementa <xref:System.Collections.IEnumerable> que contém um método `Add` com vários parâmetros permite inicializadores de coleção com vários elementos por item na lista correspondente à assinatura do método `Add`. 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 Os métodos `Add` podem usar a palavra-chave `params` para ter um número variável de argumentos como mostrado no seguinte exemplo. Este exemplo demonstra a implementação personalizada de um indexador para inicializar uma coleção usando indexadores.
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
