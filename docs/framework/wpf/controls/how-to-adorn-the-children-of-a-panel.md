---
title: 'Como: Adornar os filhos de um painel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 9f840180edf55c3e10e6859dfc2b9f4b6495b878
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358179"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>Como: Adornar os filhos de um painel
Este exemplo mostra como programaticamente associar um adorno aos filhos de um especificado <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Exemplo  
 Para associar um adorno aos filhos de um <xref:System.Windows.Controls.Panel>, siga estas etapas:  
  
1.  Declare uma nova <xref:System.Windows.Documents.AdornerLayer> objeto e a chamada a `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> método para encontrar uma camada de adorno para o elemento cujos filhos serão adornados.  
  
2.  Enumere todos os filhos do elemento pai e chamada o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar um adorno a cada elemento filho.  
  
 O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) aos filhos de um <xref:System.Windows.Controls.StackPanel> nomeado *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de adornos](adorners-overview.md)
