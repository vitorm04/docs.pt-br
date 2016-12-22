---
title: "abstract (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "abstract"
  - "abstract_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave abstract [C#]"
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# abstract (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `abstract` modificadora indica que a coisa que está sendo modificada tem uma implementação incompleta ou ausente.  O abstract modificador pode ser usado com classes, métodos, propriedades, indexadores, e eventos  Use o `abstract` modificador em uma declaração de classe para indicar que uma classe destina\-se somente a ser uma classe base de outras classes.  Membros marcados como Abstract, ou incluídos em uma classe abstrata, devem ser implementados pelas classes que derivam da classe abstrata.  
  
## Exemplo  
 Neste exemplo, a classe `Square` deve fornecer uma implementação de `Area` porque ele deriva de `ShapesClass`:  
  
 [!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 Classes abstratas tem os seguintes recursos:  
  
-   Uma classe abstrata não pode ser instanciada.  
  
-   Uma classe abstrata pode conter métodos abstratos e assessores.  
  
-   Não é possível modificar uma classe abstrata com o [sealed](../../../csharp/language-reference/keywords/sealed.md) modificador porque os dois modifers têm um significado oposto.  O `sealed` modificador impede que uma classe sendo herdadas e o `abstract` modificador requer uma classe para ser herdada.  
  
-   Uma classe não\-abstratas derivada de uma classe abstrata deve incluir reais implementações de todos os métodos abstratos e assessores herdados.  
  
 Use o `abstract` modificador em uma declaração de método ou propriedade para indicar que o método ou propriedade não contém implementação.  
  
 Métodos abstratos ter os seguintes recursos:  
  
-   Um método Abstract é implicitamente um método virtual.  
  
-   Método Abstract declarações só são permitidas em classes abstratas.  
  
-   Porque uma declaração de método abstract não fornece nenhuma implementação real, não existe nenhum corpo de método; a declaração de método simplesmente acaba com um ponto\-e\-vírgula e não existe nenhuma chave \({ }\) seguindo a assinatura.  Por exemplo:  
  
    ```  
    public abstract void MyMethod();  
    ```  
  
     A implementação é fornecida por um método de substituição[override](../../../csharp/language-reference/keywords/override.md), que é um membro de uma classe non\-abstract.  
  
-   É um erro para usar o  [estático](../../../csharp/language-reference/keywords/static.md) ou  [virtual](../../../csharp/language-reference/keywords/virtual.md) modificadores em uma declaração de método abstract.  
  
 Propriedades abstratas se comportam como métodos abstratos, exceto para as diferenças na sintaxe declaração e chamada.  
  
-   É um erro para usar o `abstract` modificador em uma propriedade estática.  
  
-   Uma propriedade herdada abstrata pode ser substituída em uma classe derivada, incluindo uma declaração de propriedade que usa o  [Substituir](../../../csharp/language-reference/keywords/override.md) modificador.  
  
 Para obter mais informações sobre classes abstratas, consulte [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Uma classe abstrata deve fornecer implementação para todos os membros de interface.  
  
 Uma classe abstrata que implementa uma interface pode mapear os métodos interface em métodos abstratos.  Por exemplo:  
  
 [!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## Exemplo  
 Neste exemplo, a classe `DerivedClass` é derivada de uma classe `BaseClass` abstrata.  A classe abstrata contém um método Abstract, `AbstractMethod`,. e duas propriedades `X` abstratas e `Y`  
  
 [!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 No exemplo anterior se você tentar criar a classe abstrata usando uma instrução como este:  
  
```  
BaseClass bc = new BaseClass();   // Error  
```  
  
 Você receberá um erro informando que o compilador Não é possível criar uma instância da classe abstrata ' BaseClass '.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)