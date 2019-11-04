---
title: Como tornar um congelável somente leitura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460077"
---
# <a name="how-to-make-a-freezable-read-only"></a>Como tornar um congelável somente leitura
Este exemplo mostra como tornar um <xref:System.Windows.Freezable> somente leitura chamando seu método <xref:System.Windows.Freezable.Freeze%2A>.  
  
 Você não poderá congelar um objeto <xref:System.Windows.Freezable> se qualquer uma das condições a seguir for `true` sobre o objeto:  
  
- Ele tem propriedades animadas ou associadas a dados.  
  
- Ele tem propriedades que são definidas por um recurso dinâmico. Para obter mais informações sobre recursos dinâmicos, consulte os [recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Ele contém <xref:System.Windows.Freezable> subobjetos que não podem ser congelados.  
  
 Se essas condições forem `false`das para o objeto <xref:System.Windows.Freezable> e você não pretender modificá-lo, considere a possibilidade de congelá-lo para obter benefícios de desempenho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir congela um <xref:System.Windows.Media.SolidColorBrush>, que é um tipo de objeto <xref:System.Windows.Freezable>.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Para obter mais informações sobre objetos <xref:System.Windows.Freezable>, consulte a [visão geral dos objetos Freezable](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Visão geral de objetos congeláveis](freezable-objects-overview.md)
- [Tópicos explicativos](base-elements-how-to-topics.md)
