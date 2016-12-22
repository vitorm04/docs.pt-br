---
title: "Tipos de valor (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.valuetypes"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Linguagem C#, tipos de valor"
  - "tipos [C#], tipos de valor"
  - "tipos de valor [C#]"
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tipos de valor (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Tipos de valor consiste em duas categorias principais:  
  
-   [Estruturas](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Enumerações](../../../csharp/language-reference/keywords/enum.md)  
  
 Queda de Estruturas em essas categorias:  
  
-   tipos numéricos  
  
    -   [tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [tipos de ponto flutuante](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   Estruturas definidos pelo usuário.  
  
## Recursos chave de tipos de valor  
 Variáveis que são baseados em tipos de valor diretamente contêm valores.  Atribuindo uma variável do tipo de valor para outro copia o valor contido.  Isso difere da atribuição de variável de tipo de referência, que copia uma referência ao objeto mas não para o objeto.  
  
 Todos os tipos de valor são derivados de <xref:System.ValueType?displayProperty=fullName>implicitamente.  
  
 A o contrário com tipos de referência, você não pode derivar um novo tipo de um tipo de valor.  Em o entanto, como a referência tipos, estruturas podem implementar interfaces.  
  
 A o contrário dos tipos de referência, um tipo de valor não pode conter o valor de `null` .  Em o entanto, o recurso de [tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md) permite tipos de valor a ser atribuído a `null`.  
  
 Cada tipo de valor tem um construtor padrão implícito que inicializa o valor padrão de esse tipo.  Para obter informações sobre valores padrões de tipos de valor, consulte [Tabela dos valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## Recursos chave de tipos simples  
 todos os tipos simples \-\- isso integral a linguagem C\# \-\- são alias de tipos do .NET Framework.  Por exemplo, [int](../../../csharp/language-reference/keywords/int.md) é um alias de <xref:System.Int32?displayProperty=fullName>.  Para obter uma lista completa do alias, consulte [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 As expressões constantes, cujos os operandos são todas as constantes do tipo simples, são avaliadas em tempo de compilação.  
  
 Os tipos simples podem ser inicializados usar literais.  Por exemplo, “A” é um tipo literal de `char` e 2001 é um literal de tipo `int`.  
  
## inicializando tipos de valor  
 Variáveis locais em C\# devem ser inicializados antes que eles sejam usados.  Por exemplo, você pode declarar uma variável local sem inicialização como no exemplo a seguir:  
  
```  
int myInt;  
```  
  
 Você não pode usá\-lo antes do inicializa.  Você pode inicializá\-la usando a instrução a seguir:  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Essa instrução é equivalente para a instrução a seguir:  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 Você pode, é claro, ter a declaração e a inicialização na mesma instrução que os exemplos seguintes:  
  
```  
int myInt = new int();  
```  
  
 \- ou \-  
  
```  
int myInt = 0;  
```  
  
 Usando o operador de [novo](../../../csharp/language-reference/keywords/new.md) chama o construtor padrão do tipo específico e atribui o valor padrão para a variável.  Em o exemplo anterior, o construtor padrão atribuído um valor o `0` a `myInt`.  Para obter mais informações sobre os valores atribuídos chamando construtores padrão, consulte [Tabela dos valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Com tipos definidos pelo usuário, use [novo](../../../csharp/language-reference/keywords/new.md) para chamar o construtor padrão.  Por exemplo, a seguinte declaração chama o construtor padrão de estrutura de `Point` :  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Após esta chamada, a estrutura é considerado ser atribuído definida; isto é, todos os seus membros são inicializadas para seus valores padrão.  
  
 Para obter mais informações sobre o novo operador, consulte [novo](../../../csharp/language-reference/keywords/new.md).  
  
 Para obter informações sobre como formatar a saída de tipos numéricos, consulte [Formatação numérica resultados da tabela](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [Tabelas de referência de tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)