---
title: Trabalhando com objetos dinâmicos
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 20d007fb48e1db352bab6d8e25d2e60e02554732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345170"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Trabalhando com objetos dinâmicos (Visual Basic)
Os objetos dinâmicos fornecem outra maneira, além do tipo de `Object`, para associar tardiamente a um objeto em tempo de execução. Um objeto dinâmico expõe Membros como propriedades e métodos em tempo de execução usando interfaces dinâmicas que são definidas no namespace <xref:System.Dynamic>. Você pode usar as classes no namespace <xref:System.Dynamic> para criar objetos que funcionam com estruturas de dados que não correspondem a um tipo ou formato estático. Você também pode usar os objetos dinâmicos que são definidos em linguagens dinâmicas, como IronPython e IronRuby. Para obter exemplos que mostram como criar objetos dinâmicos ou usar um objeto dinâmico definido em uma linguagem dinâmica, consulte [Walkthrough: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>ou <xref:System.Dynamic.ExpandoObject>.  
  
 O Visual Basic é associado a objetos do tempo de execução de linguagem dinâmica e linguagens dinâmicas, como IronPython e IronRuby, usando a interface <xref:System.Dynamic.IDynamicMetaObjectProvider>. Exemplos de classes que implementam a interface `IDynamicMetaObjectProvider` são as classes <xref:System.Dynamic.DynamicObject> e <xref:System.Dynamic.ExpandoObject>.  
  
 Se uma chamada de associação tardia for feita em um objeto que implementa a interface `IDynamicMetaObjectProvider`, Visual Basic será associado ao objeto dinâmico usando essa interface. Se uma chamada de ligação tardia for feita em um objeto que não implementa a interface de `IDynamicMetaObjectProvider`, ou se a chamada à interface de `IDynamicMetaObjectProvider` falhar, o Visual Basic será associado ao objeto usando os recursos de ligação tardia do tempo de execução do Visual Basic.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [Passo a passo: Criando e usando objetos dinâmicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Associação Antecipada e Tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
