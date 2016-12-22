---
title: "static (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "static"
  - "static_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave static [C#]"
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# static (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Use o `static` modificador para declarar um membro estático, que pertence ao tipo de si mesmo, em vez de um objeto específico.  O `static` modificador pode ser usado com classes, campos, métodos, propriedades, operadores, eventos e construtores, mas ele não pode ser usado com tipos diferentes de classes, destruidores ou indexadores.  Para obter mais informações, consulte [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## Exemplo  
 A seguinte classe é declarada como `static` e contém somente `static` métodos:  
  
 [!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 Uma declaração de constante ou tipo é implicitamente um membro estático.  
  
 Um membro static não pode ser referenciado por uma instância.  Em vez disso, ele é referido através o nome do tipo.  Por exemplo, considere a seguinte classe:  
  
 [!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 Para referir\-se ao membro estático `x`, use o nome totalmente qualificado, `MyBaseC.MyStruct.x`, a menos que o membro é acessível a partir do mesmo escopo:  
  
```c#  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 Enquanto uma instância de uma classe contém uma cópia separada de todos os campos da instância da classe, existe apenas uma cópia de cada campo estático.  
  
 Não é possível usar  [Este](../../../csharp/language-reference/keywords/this.md) para fazer referência a métodos estáticos ou os assessores da propriedade.  
  
 Se a `static` palavra\-chave é aplicado a uma classe, todos os membros da classe devem ser estáticos.  
  
 Classes e classes estáticas podem ter construtores estáticos.  Construtores estáticos são chamados em algum ponto entre o início do programa e quando a classe é instanciada.  
  
> [!NOTE]
>  O `static` palavra\-chave mais limitou usos que em C\+\+.  Para comparar com a palavra\-chave do C\+\+, consulte [Estático](/visual-cpp/misc/static-cpp).  
  
 Para demonstrar estáticos membros, considere uma classe que represente um funcionário da empresa.  Suponha que a classe contém um método para funcionários de contagem e um campo para armazenar o número de funcionários.  O método e o campo não pertencem a qualquer funcionário da instância.  Em vez deles pertence à classe da empresa.  Portanto, eles devem ser declarados como membros de classe estáticos.  
  
## Exemplo  
 Este exemplo lê o nome e identificação de um novo funcionário, incrementa o contador do funcionário por um e exibe as informações para o novo funcionário e o novo número de funcionários.  Para simplificar, este programa lê o número atual de funcionários por meio do teclado.  Em um aplicativo real, essas informações devem ser ler de um arquivo.  
  
 [!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## Exemplo  
 Este exemplo mostra que embora você possa inicializar um campo estático usando outro campo estático que ainda não foi declarado, os resultados serão indefinidos até que você atribuir explicitamente um valor para o campo estático.  
  
 [!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)