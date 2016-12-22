---
title: "Recursos do C# que d&#227;o suporte a LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], recursos que dão suporte a LINQ"
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Recursos do C# que d&#227;o suporte a LINQ
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A seção a seguir apresenta novas construções de linguagem, introduzidas no c\# 3.0. Embora esses novos recursos são usados em um nível com [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas, eles não estão limitados a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] e pode ser usado em qualquer contexto onde você encontrá\-los úteis.  
  
## Expressões de consulta  
 Expressões de consultas usam uma sintaxe declarativa semelhante ao SQL ou XQuery para consultar sobre coleções IEnumerable. Na compilação sintaxe de consulta de hora é convertida em chamadas de método para um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] a implementação do provedor de métodos de extensão de operador de consulta padrão. Os aplicativos controlam os operadores de consulta padrão que estão no escopo, especificando o namespace apropriado com um `using` diretiva. A expressão de consulta a seguir pega uma matriz de cadeias de caracteres, agrupa\-os de acordo com o primeiro caractere na cadeia de caracteres e ordena os grupos.  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 Para obter mais informações, consulte [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## Implicitamente variáveis tipadas \(var\)  
 Em vez de especificar explicitamente um tipo quando declarar e inicializar uma variável, você pode usar o [var](../../../../csharp/language-reference/keywords/var.md) modificador para instruir o compilador inferir e atribuir o tipo, conforme mostrado aqui:  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 As variáveis declaradas como `var` são apenas como fortemente tipado como variáveis cujo tipo você especificar explicitamente. O uso de `var` torna possível criar tipos anônimos, mas pode ser usado para qualquer variável local. Matrizes também podem ser declaradas com digitação implícita.  
  
 Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## Inicializadores de objeto e coleção  
 Inicializadores de objeto e coleção tornam possível inicializar objetos sem chamar explicitamente um construtor para o objeto. Inicializadores normalmente são usados em expressões de consulta quando eles projetam os dados de origem para um novo tipo de dados. Supondo que uma classe chamada `Customer` com pública `Name` e `Phone` Propriedades, o inicializador de objeto podem ser usadas como o código a seguir:  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 Para obter mais informações, consulte [Inicializadores de objeto e coleção](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## Tipos anônimos  
 Um tipo anônimo é criado pelo compilador e o nome do tipo só está disponível para o compilador. Tipos anônimos fornecem uma maneira conveniente de agrupar um conjunto de propriedades temporariamente em um resultado de consulta sem a necessidade de definir um diferente tipo nomeado. Tipos anônimos são inicializados com uma nova expressão e um inicializador de objeto, como mostrado aqui:  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 Para obter mais informações, consulte [Tipos anônimos](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## Métodos de extensão  
 Um método de extensão é um método estático que pode ser associado um tipo, para que possa ser chamado como se fosse um método de instância no tipo. Esse recurso permite que você, na verdade, "Adicionar" novos métodos para tipos existentes sem realmente modificá\-los. Os operadores de consulta padrão são um conjunto de métodos de extensão que fornecem [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] funcionalidade de consulta para qualquer tipo que implemente <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Para obter mais informações, consulte [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## Expressões lambda  
 Uma expressão lambda é uma função embutida que usa o \= \> operador para separar os parâmetros do corpo da função de entrada e podem ser convertidos em tempo de compilação para um delegado ou uma árvore de expressão. Em [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] de programação, você encontrará as expressões lambda ao fazer chamadas de método direto para os operadores de consulta padrão.  
  
 Para obter mais informações, consulte:  
  
-   [Funções anônimas](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Expressões lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [Árvores de expressão \(c\#\)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## Propriedades autoimplementadas  
 Propriedades autoimplementadas Verifique a declaração de propriedade mais concisa. Quando você declara uma propriedade, conforme mostrado no exemplo a seguir, o compilador criará um campo de backup particular, anônimos que não é acessível, exceto por meio da propriedade getter e setter.  
  
```  
public string Name {get; set;}  
```  
  
 Para obter mais informações, consulte [Propriedades autoimplementadas](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## Consulte também  
 [Consulta integrada à linguagem \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/index.md)