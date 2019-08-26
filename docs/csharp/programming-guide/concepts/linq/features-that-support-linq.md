---
title: funcionalidades do C# que dão suporte a LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 1029d34ae8823fe91c7e4bc92e168fcc1061c707
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594407"
---
# <a name="c-features-that-support-linq"></a>funcionalidades do C# que dão suporte a LINQ

A seção a seguir apresenta os novos constructos de linguagem introduzidos no C# 3.0. Embora esses novos recursos tenham algum grau de utilização com consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], eles não estão limitados a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] e podem ser usados em qualquer contexto em que sejam úteis.

## <a name="query-expressions"></a>Expressões de consulta

As expressões de consulta usam uma sintaxe declarativa semelhante ao SQL ou XQuery para consultar em coleções IEnumerable. Em tempo de compilação, a sintaxe de consulta é convertida em chamadas de método a uma implementação da [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dos métodos de extensão do operador de consulta padrão do provedor. Os aplicativos controlam os operadores de consulta padrão que estão no escopo, especificando o namespace apropriado com uma diretiva `using`. A expressão de consulta a seguir pega uma matriz de cadeias de caracteres, agrupa-os de acordo com o primeiro caractere da cadeia de caracteres e ordena os grupos.

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

Para obter mais informações, consulte [Expressões de Consulta LINQ](../../linq-query-expressions/index.md).

## <a name="implicitly-typed-variables-var"></a>Variáveis tipadas implicitamente (var)

Em vez de especificar explicitamente um tipo ao declarar e inicializar uma variável, você pode usar o modificador [var](../../../language-reference/keywords/var.md) para instruir o compilador a inferir e atribuir o tipo, conforme mostrado aqui:

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

As variáveis declaradas como `var` são tão fortemente tipadas quanto as variáveis cujo tipo você especifica explicitamente. O uso de `var` possibilita a criação de tipos anônimos, mas ele pode ser usado para quaisquer variáveis locais. As matrizes também podem ser declaradas com tipagem implícita.

Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Inicializadores de objeto e coleção

Os inicializadores de objeto e de coleção possibilitam a inicialização de objetos sem chamar explicitamente um construtor para o objeto. Os inicializadores normalmente são usados em expressões de consulta quando projetam os dados de origem em um novo tipo de dados. Supondo uma classe chamada `Customer` com propriedades públicas `Name` e `Phone`, o inicializador de objeto pode ser usado como no código a seguir:

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

Continuando com a nossa classe `Customer`, suponha que haja uma fonte de dados chamada `IncomingOrders` e que, para cada ordem com um grande `OrderSize`, desejamos criar um novo `Customer` com base fora dessa ordem. Uma consulta LINQ pode ser executada nessa fonte de dados e usar a inicialização do objeto para preencher uma coleção:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

A fonte de dados pode ter mais propriedades escondidas do que a classe `Customer`, como `OrderSize`, mas com a inicialização do objeto, os dados retornados da consulta são moldados no tipo de dados desejado; escolhemos os dados que são relevantes para nossa classe. Consequentemente, agora temos um `IEnumerable` preenchido com os novos `Customer`s que queríamos. O trecho acima também pode ser escrito na sintaxe de método do LINQ:

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Para obter mais informações, consulte:

- [Inicializadores de objeto e coleção](../../classes-and-structs/object-and-collection-initializers.md)

- [Sintaxe de Expressão de Consulta para Operadores de Consulta Padrão](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Tipos anônimos

Um tipo anônimo é construído pelo compilador e o nome do tipo só fica disponível para o compilador. Os tipos anônimos fornecem uma maneira conveniente de agrupar um conjunto de propriedades temporariamente em um resultado de consulta, sem a necessidade de definir um tipo nomeado separado. Os tipos anônimos são inicializados com uma nova expressão e um inicializador de objeto, como mostrado aqui:

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Para obter mais informações, consulte [Tipos anônimos](../../classes-and-structs/anonymous-types.md).

## <a name="extension-methods"></a>Métodos de extensão

Um método de extensão é um método estático que pode ser associado a um tipo, para que ele possa ser chamado como se fosse um método de instância no tipo. Esse recurso permite que você, na verdade, "adicione" novos métodos a tipos existentes sem realmente modificá-los. Os operadores de consulta padrão são um conjunto de métodos de extensão que fornecem a funcionalidade de consulta da [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para qualquer tipo que implementa a <xref:System.Collections.Generic.IEnumerable%601>.

Para obter mais informações, consulte [Métodos de extensão](../../classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Expressões lambda

Uma expressão lambda é uma função embutida que usa o operador => para separar os parâmetros de entrada do corpo da função e podem ser convertidos em um delegado ou uma árvore de expressão, em tempo de compilação. Na programação [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você encontrará as expressões lambda ao fazer chamadas de método diretas aos operadores de consulta padrão.

Para obter mais informações, consulte:

- [Funções Anônimas](../../statements-expressions-operators/anonymous-functions.md)

- [Expressões Lambda](../../statements-expressions-operators/lambda-expressions.md)

- [Árvores de expressão (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Consulte também

- [LINQ (consulta integrada à linguagem) (C#)](./index.md)
