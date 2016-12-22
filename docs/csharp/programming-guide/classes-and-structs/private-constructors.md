---
title: "Construtores particulares (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, construtores privados"
  - "construtores privados [C#]"
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Construtores particulares (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um construtor particular é um construtor de instância especial.  Ele é geralmente usado em classes que contêm apenas membros estáticos.  Se uma classe tem um ou mais construtores particulares e nenhum construtor público, outras classes \(exceto classes aninhadas\) não é possível criar instâncias dessa classe.  Por exemplo:  
  
 [!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 A declaração do construtor vazio impede que a geração automática de um construtor padrão.  Observe que se você não usar um modificador de acesso com o construtor ainda será privado por padrão.  No entanto, o  [particular](../../../csharp/language-reference/keywords/private.md) modificador geralmente é usado explicitamente para torná\-la desmarque que a classe não pode ser instanciada.  
  
 Construtores particulares são usadas para evitar a criação de instâncias de uma classe quando não existem campos de instância ou métodos, como o <xref:System.Math> classe, ou quando um método é chamado para obter uma instância de uma classe.  Se todos os métodos na classe são estáticos, considere a classe completa estático.  Para obter mais informações, consulte: [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## Exemplo  
 Este é um exemplo de uma classe usando um construtor particular.  
  
 [!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 Observe que se a instrução do exemplo a seguir, ele irá gerar um erro porque o construtor é inacessível devido a seu nível de proteção:  
  
 [!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Destruidores](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [public](../../../csharp/language-reference/keywords/public.md)