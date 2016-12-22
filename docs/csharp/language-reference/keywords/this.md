---
title: "this (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "this"
  - "this_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave this [C#]"
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# this (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `this` refere\-se à instância atual da classe de palavra\-chave e também é usado como um modificador do primeiro parâmetro de um método de extensão.  
  
> [!NOTE]
>  Este artigo discute o uso de `this` com instâncias de classe.  Para obter mais informações sobre seu uso em métodos de extensão, consulte [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
 A seguir estão os usos comuns do `this`:  
  
-   Para qualificar membros ocultados por nomes semelhantes, por exemplo:  
  
 [!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   Para passar um objeto como um parâmetro para outros métodos, por exemplo:  
  
    ```  
    CalcTax(this);  
    ```  
  
-   Para declarar indexadores, por exemplo:  
  
 [!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 Funções de membro estático, porque eles existem no nível de classe e não como parte de um objeto, não tem um `this` ponteiro.  É um erro para se referir a `this` em um método estático.  
  
## Exemplo  
 Neste exemplo, `this` é usado para qualificar o `Employee` , membros de classe `name` e `alias`, que estão ocultos por nomes semelhantes.  Ele também é usado para passar um objeto para o método `CalcTax`, que pertence a outra classe.  
  
 [!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [Métodos](../../../fsharp/language-reference/members/methods.md)