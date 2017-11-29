---
title: "Como implementar membros de duas interfaces explicitamente (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f0820328f037008c152b2e23071ae0ba8dba02bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Como implementar membros de duas interfaces explicitamente (Guia de Programação em C#)
A implementação explícita da [interface](../../../csharp/language-reference/keywords/interface.md) também permite ao programador implementar duas interfaces que têm os mesmos nomes de membro e implementar separadamente cada membro de interface. Este exemplo exibe as dimensões de uma caixa em unidades inglesas e no sistema métrico. A Caixa [classe](../../../csharp/language-reference/keywords/class.md) implementa duas interfaces, IEnglishDimensions e IMetricDimensions, que representam os diferentes sistemas de medida. As duas interfaces têm nomes de membro idênticos, Comprimento e Largura.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Caso deseje que as medidas padrão estejam unidades inglesas, implemente os métodos Comprimento e Largura normalmente e implemente explicitamente os métodos Comprimento e Largura da interface IMetricDimensions:  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 Nesse caso, é possível acessar as unidades inglesas da instância de classe e acessar as unidades métricas da instância da interface:  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)  
 [Como implementar membros de interface explicitamente](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
