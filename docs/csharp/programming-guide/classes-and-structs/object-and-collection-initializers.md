---
title: Inicializadores de objeto e coleção – Guia de Programação em C#
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 1dc28ac218eb0325095641840834b40594ad67ab
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084856"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicializadores de objeto e coleção (Guia de Programação em C#)

O C# permite criar uma instância de um objeto ou uma coleção e executar as atribuições de membro em uma única instrução.

## <a name="object-initializers"></a>Inicializadores de objeto

Os inicializadores de objeto permitem atribuir valores a quaisquer campos ou propriedades acessíveis de um objeto na hora de criação sem que seja necessário invocar um construtor seguido por linhas de instruções de atribuição. A sintaxe do inicializador de objeto permite especificar argumentos para um construtor ou omitir os argumentos (e a sintaxe de parênteses).  O exemplo a seguir mostra como usar um inicializador de objeto com um tipo nomeado `Cat` e como invocar o construtor padrão. Observe o uso de propriedades autoimplementadas na classe `Cat`. Para obter mais informações, consulte [Propriedades autoimplementadas](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
A sintaxe dos inicializadores de objetos permite que você crie uma instância, e depois atribui o objeto recém-criado, com suas propriedades atribuídas, à variável na atribuição.

Começando com o C# 6, os inicializadores de objeto podem definir indexadores, além de atribuir campos e propriedades. Considere esta classe `Matrix` básica:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Você poderia inicializar a matriz de identidade com o código a seguir:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Nenhum indexador acessível que contenha um setter acessível pode ser usado como uma das expressões no inicializador de objeto, independentemente do número ou dos tipos de argumentos. Os argumentos de índice formam o lado esquerdo da atribuição e o valor é o lado direito da expressão.  Por exemplo, estes serão todos válidos se `IndexersExample` tiver os indexadores apropriados:

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Baz = Math.PI,
    ['C',4] = "Middle C"
}
```

Para que o código anterior seja compilado, o tipo `IndexersExample` precisará ter os seguintes membros:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
}
```

## <a name="object-initializers-with-anonymous-types"></a>Inicializadores de objeto com tipos anônimos

Embora inicializadores de objetos possam ser usados em qualquer contexto, eles são especialmente úteis em expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Expressões de consulta fazem uso frequente de [tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), que podem ser inicializados somente usando um inicializador de objeto, como mostrado na declaração a seguir.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Os tipos anônimos habilitam a cláusula `select` em uma expressão de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a transformar objetos da sequência original em objetos cujo valor e forma podem diferir dos originais. Isso será útil se você desejar armazenar apenas uma parte das informações de cada objeto em uma sequência. No exemplo a seguir, suponha que um objeto de produto (`p`) contenha vários campos e métodos e que você esteja apenas interessado em criar uma sequência de objetos que contenha o nome do produto e o preço unitário.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Quando essa consulta for executada, a variável `productInfos` conterá uma sequência de objetos que podem ser acessados em uma instrução `foreach` como mostrado neste exemplo:  

```csharp
foreach(var p in productInfos){...}  
```

Cada objeto no novo tipo anônimo tem duas propriedades públicas que recebem os mesmos nomes que as propriedades ou os campos no objeto original. Você também poderá renomear um campo quando estiver criando um tipo anônimo; o exemplo a seguir renomeia o campo `UnitPrice` como `Price`.  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Inicializadores de coleção

Os inicializadores de coleção permitem especificar um ou mais inicializadores de elemento quando você inicializa um tipo de coleção que implementa <xref:System.Collections.IEnumerable> e tem `Add` com a assinatura apropriada como um método de instância ou um método de extensão. Os inicializadores de elemento podem ser um valor simples, uma expressão ou um inicializador de objeto. Ao usar um inicializador de coleção, você não precisa especificar várias chamadas. O compilador adiciona as chamadas automaticamente.  
  
O exemplo a seguir mostra dois inicializadores de coleção simples:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

O inicializador de coleção a seguir usa inicializadores de objeto para inicializar objetos da classe `Cat` definida em um exemplo anterior. Observe que os inicializadores de objeto individuais são envolvidos por chaves e separados por vírgulas.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Você poderá especificar [nulo](../../language-reference/keywords/null.md) como um elemento em um inicializador de coleção se o método `Add` da coleção permitir.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 É possível especificar elementos indexados quando a coleção é compatível com indexação de leitura/gravação.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

O exemplo anterior gera o código que chama o <xref:System.Collections.Generic.Dictionary%602.Item(%600)> para definir os valores. Começando com o C# 6, você pode inicializar dicionários e outros contêineres associativos usando a seguinte sintaxe. Observe que, em vez da sintaxe do indexador, com parênteses e uma atribuição, ele usa um objeto com vários valores:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Este exemplo de inicializador chama <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> para adicionar os três itens no dicionário. Essas duas maneiras diferentes para inicializar coleções associativas tem um comportamento um pouco diferente devido às chamadas de método que o compilador gera. As duas variantes trabalham com a classe `Dictionary`. Outros tipos podem ser compatíveis apenas com uma ou com outra, dependendo da API pública deles.

## <a name="examples"></a>Exemplos

O exemplo a seguir combina os conceitos de inicializadores de coleção e objeto.

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

O exemplo a seguir mostra um objeto que implementa <xref:System.Collections.IEnumerable> e contém um método `Add` com vários parâmetros. Ele usa um inicializador de coleção com vários elementos por item na lista que correspondem à assinatura do método `Add`.

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

Os métodos `Add` podem usar a palavra-chave `params` para obter um número variável de argumentos, como mostrado no seguinte exemplo. Este exemplo também demonstra a implementação personalizada de um indexador para inicializar uma coleção usando índices.

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)  
- [Expressões de consulta LINQ](../linq-query-expressions/index.md)  
- [Tipos Anônimos](anonymous-types.md)
