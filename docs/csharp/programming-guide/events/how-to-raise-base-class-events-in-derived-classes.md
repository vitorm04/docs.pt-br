---
title: "Como acionar eventos de classe base em classes derivadas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "eventos [C#], em classes derivadas"
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como acionar eventos de classe base em classes derivadas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O simple exemplo a seguir mostra o modo padrão para declarar os eventos em uma classe base para que eles também podem ser disparados a partir de classes derivadas.  Esse padrão é usado amplamente em classes de Windows Forms na [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]bibliotecade classe.  
  
 Quando você criar uma classe que pode ser usado como uma classe base para outras classes, você deve considerar o fato de que os eventos são um tipo especial de delegado que só pode ser chamada de dentro da classe declarada\-los.  Classes derivadas não podem chamar diretamente o eventos que são declarados dentro da classe base.  Embora, às vezes, é aconselhável um evento que só pode ser gerados pela classe base, na maioria das vezes, você deve ativar a classe derivada invocar os eventos de classe base .  Para fazer isso, você pode criar um método chamar protegido na classe base que encapsula o evento.  Ligando ou substituindo a isso chamando o método, as classes derivadas podem invocar o evento indiretamente.  
  
> [!NOTE]
>  Não declarar eventos virtuais em um classe base e substituir \-los em uma classede derivada.  O C\# compilador faz não identificador esses corretamente e é imprevisível se um assinante para o evento de derivado será realmente assinando o classe basedeevento.  
  
## Exemplo  
 [!CODE [csProgGuideEvents#1](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEvents#1)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Eventos](../../../csharp/programming-guide/events/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Criando manipuladores de eventos no Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)