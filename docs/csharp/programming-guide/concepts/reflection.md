---
title: "Reflex&#227;o (c#) | Microsoft Docs"
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
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Reflex&#227;o (c#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Reflexão fornece objetos \(do tipo <xref:System.Type>\) que descrevem os assemblies, módulos e tipos. Você pode usar reflexão dinamicamente criar uma instância de um tipo, o tipo de associação a um objeto existente, ou obter o tipo de um objeto existente e chamar seus métodos ou acessar suas propriedades e campos. Se você estiver usando atributos no seu código, reflexão permite acessá\-los. Para obter mais informações, consulte [Atributos](../Topic/Extending%20Metadata%20Using%20Attributes.md).  
  
 Aqui está um exemplo simples de reflexão usando o método estático `GetType` \- herdadas por todos os tipos do `Object` base class \- para obter o tipo de uma variável:  
  
```c#  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 A saída é:  
  
 `System.Int32`  
  
 O exemplo a seguir usa a reflexão para obter o nome completo do assembly carregado.  
  
```c#  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 A saída é:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  As palavras\-chave c\# `protected` e `internal` não têm significado em IL e não são usados nas APIs de reflexão. São os termos correspondentes em IL *família* e *Assembly*. Para identificar um `internal` método usando a reflexão, uso o <xref:System.Reflection.MethodBase.IsAssembly%2A> propriedade. Para identificar um `protected internal` método, use o <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
## Visão geral de reflexão  
 A reflexão é útil nas seguintes situações:  
  
-   Quando você tem que acessar atributos nos metadados do seu programa. Para obter mais informações, consulte [Recuperando informações armazenadas em atributos](../Topic/Retrieving%20Information%20Stored%20in%20Attributes.md).  
  
-   Para examinar e instanciar tipos em um assembly.  
  
-   Para criar novos tipos em tempo de execução. Usar as classes em <xref:System.Reflection.Emit>.  
  
-   Para executar ligação tardia, acessar métodos em tipos criados em tempo de execução. Consulte o tópico [Carregando e usando tipos dinamicamente](../Topic/Dynamically%20Loading%20and%20Using%20Types.md).  
  
## Seções relacionadas  
 Para obter mais informações:  
  
-   [Reflexão](../Topic/Reflection%20in%20the%20.NET%20Framework.md)  
  
-   [Exibindo informações de tipo](../Topic/Viewing%20Type%20Information.md)  
  
-   [Reflexão e tipos genéricos](../Topic/Reflection%20and%20Generic%20Types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [Recuperando informações armazenadas em atributos](../Topic/Retrieving%20Information%20Stored%20in%20Attributes.md)  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Assemblies no Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)