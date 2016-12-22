---
title: "class (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "class_CSharpKeyword"
  - "class"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave class [C#]"
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# class (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Classes são declaradas usando a palavra\-chave `class`, conforme mostrado no exemplo o seguir:  
  
```  
  
      class TestClass  
{  
    // Methods, properties, fields, events, delegates   
    // and nested classes go here.  
}  
```  
  
## Comentários  
 Somente a única herança é permitida em C\#.  Ou seja uma classe pode herdar implementação de uma classe base somente.  No entanto, uma classe pode implementar mais de uma interface.  A tabela a seguir mostra exemplos de implementação de herança e da interface da classe:  
  
|Herança|Exemplo|  
|-------------|-------------|  
|Nenhum|`class ClassA { }`|  
|Single|`class DerivedClass: BaseClass { }`|  
|Nenhum, implementa duas interfaces|`class ImplClass: IFace1, IFace2 { }`|  
|Único, implementa uma interface|`class ImplDerivedClass: BaseClass, IFace1 { }`|  
  
 As classes que você declarar diretamente em um namespace, não aninhadas dentro de outras classes, podem ser [público](../../../csharp/language-reference/keywords/public.md) ou [interno](../../../csharp/language-reference/keywords/internal.md).  Classes são `internal` por padrão.  
  
 Membros, incluindo classes aninhadas, pode ser [público](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protegido](../../../csharp/language-reference/keywords/protected.md), [interno](../../../csharp/language-reference/keywords/internal.md), ou [private](../../../csharp/language-reference/keywords/private.md).  Os membros são [private](../../../csharp/language-reference/keywords/private.md) por padrão.  
  
 Para obter mais informações, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Você pode declarar as classes genéricas que têm parâmetros de tipo.  Para obter mais informações, consulte [Classes genéricas](../../../csharp/programming-guide/generics/generic-classes.md).  
  
 Uma classe pode conter declarações dos seguintes membros:  
  
-   [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Destructors](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Métodos](../../../fsharp/language-reference/members/methods.md)  
  
-   [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
  
-   [Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [Eventos](../../../csharp/programming-guide/events/index.md)  
  
-   [Delegados](../../../csharp/programming-guide/delegates/index.md)  
  
-   [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)  
  
-   [Estruturas](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
## Exemplo  
 O exemplo a seguir demonstra como declarar campos de classe construtores, métodos, e.  Também demonstra a instanciação do objeto e os dados da instância de impressão.  Nesse exemplo, duas classes são declarados, a classe de `Child` , que contém dois campos particulares \(`name` e `age`\) e dois métodos públicos.  A segunda classe, `StringTest`, é usada para conter `Main`.  
  
 [!CODE [csrefKeywordsTypes#5](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#5)]  
  
## Comentários  
 Observe, no exemplo anterior, os campos particulares \(`name` e `age`\) podem ser acessados com métodos públicos de classes de `Child` .  Por exemplo, você não pode imprimir o nome do filho, o método de `Main` , usando uma instrução assim:  
  
```  
Console.Write(child1.name);   // Error  
```  
  
 Acessar membros particulares de `Child` de `Main` seria possível `Main` somente se fosse um membro da classe.  
  
 Tipos declarados dentro de uma classe sem um modificador de acesso padrão a `private`, então os membros de dados nesse exemplo é ainda `private` se a palavra\-chave foi removido.  
  
 Finalmente, observe que para o objeto criado usando o construtor padrão \(`child3`\), o campo de idade foi inicializado para zero por padrão.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)