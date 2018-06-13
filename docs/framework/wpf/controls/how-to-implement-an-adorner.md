---
title: Como implementar um adorno
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: f5b0ed080a413546a3b985055858e209f9f347eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552959"
---
# <a name="how-to-implement-an-adorner"></a>Como implementar um adorno
Este exemplo mostra uma implementação mínima de adorno.  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 É importante observar que adornos não incluem nenhum comportamento de renderização inerente; garantir que um adorno seja renderizado é responsabilidade do implementador do adorno.   Uma maneira comum de implementar o comportamento de renderização é substituir a <xref:System.Windows.UIElement.OnRender%2A> método e o uso de um ou mais <xref:System.Windows.Media.DrawingContext> objetos para renderizar os visuais do adorno conforme necessário (como mostrado neste exemplo).  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Um adorno personalizado é criado com a implementação de uma classe que herda da <xref:System.Windows.Documents.Adorner> classe.  O adorno de exemplo simplesmente adorna os cantos de uma <xref:System.Windows.UIElement> com círculos, substituindo o <xref:System.Windows.UIElement.OnRender%2A> método.  
  
### <a name="code"></a>Código  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de adornos](../../../../docs/framework/wpf/controls/adorners-overview.md)
