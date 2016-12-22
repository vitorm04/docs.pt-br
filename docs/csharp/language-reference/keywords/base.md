---
title: "base (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "base"
  - "BaseClass.BaseClass"
  - "base_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave base [C#]"
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# base (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `base` palavra\-chave é usada para acessar os membros da classe base de dentro de uma classe derivada:  
  
-   Chamar um método na classe base que foi substituído por outro método.  
  
-   Especificar qual construtor da classe base deve ser chamado durante a criação de instâncias da classe derivada.  
  
 Um acesso de classe base é permitido apenas um acessador de propriedade de instância, um método de instância ou um construtor.  
  
 É um erro para usar o `base` palavra\-chave de dentro de um método estático.  
  
 A classe base que é acessada é a classe base especificada na declaração da classe.  Por exemplo, se você especificar `class ClassB : ClassA`, os membros da ClassA são acessados da ClassB, independentemente da classe base da ClassA.  
  
## Exemplo  
 Neste exemplo, tanto a classe base, `Person`e a classe derivada, `Employee`, há um método chamado `Getinfo`.  Usando o `base` palavra\-chave, é possível chamar o `Getinfo` método na classe base, de dentro da classe derivada.  
  
 [!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]  
  
 Para obter exemplos adicionais, consulte  [nova](../../../csharp/language-reference/keywords/new.md),  [virtual](../../../csharp/language-reference/keywords/virtual.md), e  [Substituir](../../../csharp/language-reference/keywords/override.md).  
  
## Exemplo  
 Este exemplo mostra como especificar o construtor da classe base chamado ao criar instâncias de uma classe derivada.  
  
 [!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [this](../../../csharp/language-reference/keywords/this.md)