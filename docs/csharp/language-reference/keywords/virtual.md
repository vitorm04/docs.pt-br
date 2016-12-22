---
title: "virtual (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "virtual_CSharpKeyword"
  - "virtual"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave virtual [C#]"
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# virtual (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `virtual` palavra\-chave é usada para modificar uma declaração de método, propriedade, indexador ou evento e permitir que ele seja substituído em uma classe derivada.  Por exemplo, este método pode ser substituído por qualquer classe que herda a ele:  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 A implementação de um membro virtual pode ser alterada por um  [substituindo o membro](../../../csharp/language-reference/keywords/override.md) em uma classe derivada.  Para obter mais informações sobre como usar o `virtual` palavra\-chave, consulte [Controle de versão com as palavras\-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [Quando usar as palavras\-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## Comentários  
 Quando um método virtual é invocado, o tipo de tempo de execução do objeto é verificado para um membro de substituição.  O substituição de membro na classe derivada mais é chamado, que pode ser o membro original, se nenhuma classe derivada substituiu o membro.  
  
 Por padrão, os métodos são não\-virtuais.  Você não pode substituir um método não\-virtual.  
  
 Não é possível usar o `virtual` modificador com o `static`, `abstract, private`, ou `override` modificadores.  O exemplo a seguir mostra uma propriedade virtual:  
  
 [!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 Propriedades virtuais se comportam como métodos abstratos, exceto pelas diferenças na sintaxe de declaração e invocação.  
  
-   É um erro para usar o `virtual` modificador em uma propriedade estática.  
  
-   Uma propriedade herdada virtual pode ser substituída em uma classe derivada, incluindo uma declaração de propriedade que usa o `override` modificador.  
  
## Exemplo  
 Neste exemplo, o `Shape` classe contém duas coordenadas `x`, `y`e o `Area()` método virtual.  Classes de forma diferente, como `Circle`, `Cylinder`, e `Sphere` herdam o `Shape` classe e a área de superfície é calculado para cada figura.  Cada classe derivada tem a suas próprias a implementação de substituição de `Area()`.  
  
 Observe que as classes herdadas `Circle`, `Sphere`, e `Cylinder` todos usam construtores inicializar a classe base, como mostrado na seguinte declaração.  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 O programa a seguir calcula e exibe a área adequada para cada figura invocando a implementação apropriada da `Area()` método, de acordo com o objeto que está associado com o método.  
  
 [!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [new](../../../csharp/language-reference/keywords/new.md)