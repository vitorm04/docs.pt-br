---
title: "Usando structs (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "estruturas [c#], usando"
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Usando structs (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `struct` tipo é adequado para representar objetos simples como `Point`, `Rectangle`, e `Color`. Embora seja conveniente representam um ponto como um [classe](../../../csharp/language-reference/keywords/class.md) com [Propriedades Auto\-Implemented](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), um [struct](../../../csharp/language-reference/keywords/struct.md) podem ser mais eficientes em alguns cenários. Por exemplo, se você declarar uma matriz de 1000 `Point` objetos, você alocará memória adicional para cada objeto de referência; nesse caso, um struct seria mais barato. Porque o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] contém um objeto chamado <xref:System.Drawing.Point>, struct neste exemplo é denominada "CoOrds" em vez disso.  
  
 [!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 É um erro ao definir um construtor \(sem parâmetros\) padrão para um struct. Também é um erro ao inicializar um campo de instância em um corpo de struct. Você pode inicializar membros de struct usando um construtor com parâmetros ou acessar os membros individualmente depois que a estrutura é declarada. Todos os membros particulares ou inacessíveis podem ser inicializados somente em um construtor.  
  
 Quando você cria um objeto de struct usando o [novo](../../../csharp/language-reference/keywords/new.md) operador, é criado e o construtor apropriado é chamado. Diferentemente das classes, structs pode ser instanciadas sem usar o `new` operador. Nesse caso, não há nenhuma chamada de construtor, que torna a alocação mais eficiente. No entanto, os campos permanecem não atribuídos e o objeto não pode ser usado até que todos os campos são inicializados.  
  
 Quando um struct contém um tipo de referência como um membro, o construtor padrão do membro deve ser chamado explicitamente, caso contrário, o membro permanece não atribuído e a estrutura não pode ser usada. \(Isso resulta em erro do compilador CS0171.\)  
  
 Não há nenhuma herança para estruturas como há para classes. Uma estrutura não pode herdar de outra estrutura ou classe, e não pode ser a base de uma classe. Estruturas, no entanto, herdarem da classe base <xref:System.Object>. Um struct pode implementar interfaces, e ele faz isso exatamente como classes.  
  
 Você não pode declarar uma classe usando a palavra\-chave `struct`. No c\#, classes e estruturas são semanticamente diferentes. Uma estrutura é um tipo de valor, enquanto uma classe é um tipo de referência. Para obter mais informações, consulte [tipos de valor](../../../csharp/language-reference/keywords/value-types.md).  
  
 A menos que você precisa de semântica de tipo de referência, uma pequena classe pode ser tratada com mais eficiência pelo sistema se você declará\-la como uma estrutura em vez disso.  
  
## Exemplo 1  
  
### Descrição  
 Este exemplo demonstra `struct` inicialização usando construtores parametrizados e padrão.  
  
### Código  
 [!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-cs[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## Exemplo 2  
  
### Descrição  
 Este exemplo demonstra um recurso que é exclusivo para estruturas. Ele cria um objeto CoOrds sem usar o `new` operador. Se você substituir a palavra `struct` com a palavra `class`, o programa não será compilado.  
  
### Código  
 [!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-cs[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)