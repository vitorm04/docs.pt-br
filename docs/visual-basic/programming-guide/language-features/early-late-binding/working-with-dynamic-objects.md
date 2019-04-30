---
title: Trabalhando com objetos dinâmicos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: ea7d7aae1cd79a0243a9c721b5e3958fba82f84f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973180"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Trabalhando com objetos dinâmicos (Visual Basic)
Objetos dinâmicos oferecem outra maneira, exceto o `Object` tipo, a associação tardia a um objeto em tempo de execução. Um objeto dinâmico expõe membros como métodos e propriedades em tempo de execução usando interfaces dinâmicas são definidos na <xref:System.Dynamic> namespace. Você pode usar as classes de <xref:System.Dynamic> namespace para criar objetos que trabalhar com estruturas de dados que não correspondem a um formato ou tipo estático. Você também pode usar os objetos dinâmicos que são definidos em linguagens dinâmicas como IronPython e IronRuby. Para obter exemplos que mostram como criar objetos dinâmicos ou usar um objeto dinâmico definido em uma linguagem dinâmica, consulte [passo a passo: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, ou <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic associa a objetos de tempo de execução de linguagem dinâmica e linguagens dinâmicas como IronPython e IronRuby usando o <xref:System.Dynamic.IDynamicMetaObjectProvider> interface. Exemplos de classes que implementam o `IDynamicMetaObjectProvider` interface são os <xref:System.Dynamic.DynamicObject> e <xref:System.Dynamic.ExpandoObject> classes.  
  
 Se for feita uma chamada de associação tardia a um objeto que implementa o `IDynamicMetaObjectProvider` da interface, associações de Visual Basic para o objeto dinâmico por meio dessa interface. Se for feita uma chamada de associação tardia a um objeto que implementa o `IDynamicMetaObjectProvider` interface, ou se a chamada para o `IDynamicMetaObjectProvider` interface falha, o Visual Basic é associado ao objeto, usando os recursos de associação tardia do tempo de execução do Visual Basic.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [Passo a passo: Criar e usar objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Associação Antecipada e Tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
