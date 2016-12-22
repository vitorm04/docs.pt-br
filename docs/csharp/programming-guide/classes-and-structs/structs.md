---
title: "Structs (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
helpviewer_keywords: 
  - "Linguagem C#, estruturas"
  - "estruturas [C#]"
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Structs (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Structs são definidos usando o  [struct](../../../csharp/language-reference/keywords/struct.md) palavra\-chave, por exemplo:  
  
 [!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 Structs compartilham a mesma sintaxe como classes, a maioria, embora a structs são mais limitados que classes:  
  
-   No prazo de uma declaração struct, campos não podem ser inicializados menos que elas são declaradas como const ou static.  
  
-   Uma struct não pode declarar um construtor padrão \(um construtor sem parâmetros\) ou um destruidor.  
  
-   Structs são copiados na atribuição.  Quando uma estrutura é atribuída a uma nova variável, todos os dados são copiados e qualquer modificação na nova cópia, não é refletida na estrutura original.  Isso é importante lembrar\-se ao trabalhar com coleções de tipos de valor, como um Dictionary \< string, myStruct \>.  
  
-   As estruturas são do tipo valor e classes são do tipo referência.  
  
-   Diferentemente das classes, structs pode ser instanciada sem usar um `new` operador.  
  
-   Structs pode declarar construtores com parâmetros.  
  
-   Uma estrutura não pode herdar uma outra estrutura ou classe, e tambem não pode ser base de uma classe.  Structs herdar diretamente de `System.ValueType`, que herda de `System.Object`.  
  
-   Uma estrutura pode implementar interfaces.  
  
-   Uma structura pode ser usada como um tipo anulável e pode ser atribuída um valor nulo.  
  
## Seções relacionadas  
 Para obter mais informações:  
  
-   [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Como saber a diferença entre passar um struct e passar uma referência de classe para um método](../Topic/How%20to:%20Know%20the%20Difference%20Between%20Passing%20a%20Struct%20and%20Passing%20a%20Class%20Reference%20to%20a%20Method%20\(C%23%20Programming%20Guide\).md)  
  
-   [Como implementar conversões definidas pelo usuário entre structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [Mais informações sobre variáveis de](http://go.microsoft.com/fwlink/?LinkId=221230) na [início 2010 do Visual C\#](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)