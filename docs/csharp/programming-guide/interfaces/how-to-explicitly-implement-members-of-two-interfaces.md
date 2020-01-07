---
title: Como implementar explicitamente membros de duas interfaces – guia C# de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 720e265cedcf9ad8be00f5e013365129f38749af
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635243"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Como implementar explicitamente membros de duas interfaces (guiaC# de programação)
A implementação explícita da [interface](../../language-reference/keywords/interface.md) também permite ao programador implementar duas interfaces que têm os mesmos nomes de membro e implementar separadamente cada membro de interface. Este exemplo exibe as dimensões de uma caixa em unidades inglesas e no sistema métrico. A Caixa [classe](../../language-reference/keywords/class.md) implementa duas interfaces, IEnglishDimensions e IMetricDimensions, que representam os diferentes sistemas de medida. As duas interfaces têm nomes de membro idênticos, Comprimento e Largura.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>Programação Robusta  
 Caso deseje que as medidas padrão estejam unidades inglesas, implemente os métodos Comprimento e Largura normalmente e implemente explicitamente os métodos Comprimento e Largura da interface IMetricDimensions:  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 Nesse caso, é possível acessar as unidades inglesas da instância de classe e acessar as unidades métricas da instância da interface:  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Classes e Structs](../classes-and-structs/index.md)
- [Interfaces](./index.md)
- [Como implementar explicitamente membros de interface](./how-to-explicitly-implement-interface-members.md)
