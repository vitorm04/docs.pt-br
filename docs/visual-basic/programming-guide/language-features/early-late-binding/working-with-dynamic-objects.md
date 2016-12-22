---
title: "Trabalhando com objetos din&#226;micos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "objetos dinâmicos [Visual Basic]"
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Trabalhando com objetos din&#226;micos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Objetos dinâmicos oferecem uma outra maneira, seja o `Object` o tipo, ligação tardia a um objeto em tempo de execução.  Um objeto dinâmico expõe os membros como, por exemplo, propriedades e métodos em tempo de execução usando interfaces dinâmicas que são definidos na <xref:System.Dynamic> espaço para nome.  Você pode usar as classes na <xref:System.Dynamic> espaço para nome para criar objetos que funcionam com estruturas de dados que não correspondem a um formato ou tipo estático.  Você também pode usar os objetos dinâmicos que são definidos em linguagens dinâmicas como, por exemplo, IronPython e IronRuby.  Para obter exemplos que mostram como criar objetos dinâmicos ou usar um objeto dinâmico definido em uma linguagem dinâmica, consulte [Passo a passo: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, ou <xref:System.Dynamic.ExpandoObject>.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]vincula\-se aos objetos de runtime de linguagem dinâmica e linguagens dinâmicas como, por exemplo, IronPython e IronRuby usando o <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.  Exemplos de classes que implementam o `IDynamicMetaObjectProvider` interface são o <xref:System.Dynamic.DynamicObject> e <xref:System.Dynamic.ExpandoObject> classes.  
  
 Se uma chamada de ligação tardia é feita para um objeto que implementa o `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] vincula\-se ao objeto dinâmico por meio dessa interface.  Se for feita uma chamada de ligação tardia a um objeto que implementa o `IDynamicMetaObjectProvider` interface, ou se a chamada para o `IDynamicMetaObjectProvider` interface falhar, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é vinculado ao objeto, usando os recursos de ligação atrasada da [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] em tempo de execução.  
  
## Consulte também  
 <xref:System.Dynamic.DynamicObject>   
 <xref:System.Dynamic.ExpandoObject>   
 [Passo a passo: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)   
 [Associação antecipada e tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)