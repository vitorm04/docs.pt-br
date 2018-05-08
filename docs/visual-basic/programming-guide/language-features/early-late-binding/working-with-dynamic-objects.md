---
title: Trabalhando com objetos dinâmicos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 78b17a379ea219cc24842322703caaa9d29eeb2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Trabalhando com objetos dinâmicos (Visual Basic)
Objetos dinâmicos oferecem uma outra maneira, que o `Object` tipo de associação tardia a um objeto em tempo de execução. Um objeto dinâmico expõe membros, como métodos e propriedades em tempo de execução usando interfaces dinâmicos que são definidas no <xref:System.Dynamic> namespace. Você pode usar as classes de <xref:System.Dynamic> namespace para criar objetos de trabalhar com estruturas de dados que não correspondem a um formato ou tipo estático. Você também pode usar os objetos dinâmicos que são definidos em linguagens dinâmicas, como o IronPython e IronRuby. Para obter exemplos que mostram como criar objetos dinâmicos ou usar um objeto dinâmico definido em linguagem dinâmica, consulte [passo a passo: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, ou <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic associa a objetos do tempo de execução de linguagem dinâmica e linguagens dinâmicas, como o IronPython e IronRuby usando o <xref:System.Dynamic.IDynamicMetaObjectProvider> interface. Exemplos de classes que implementam o `IDynamicMetaObjectProvider` interface são o <xref:System.Dynamic.DynamicObject> e <xref:System.Dynamic.ExpandoObject> classes.  
  
 Se for feita uma chamada de associação tardia a um objeto que implementa o `IDynamicMetaObjectProvider` interface Visual Basic é associado ao objeto dinâmico por meio dessa interface. Se for feita uma chamada de associação tardia a um objeto que implementa o `IDynamicMetaObjectProvider` interface, ou se a chamada para o `IDynamicMetaObjectProvider` interface falha, Visual Basic associa ao objeto, usando os recursos de associação tardia de execução do Visual Basic.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [Passo a passo: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [Associação Antecipada e Tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
