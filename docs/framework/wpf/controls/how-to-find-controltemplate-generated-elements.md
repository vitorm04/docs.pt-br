---
title: 'Como: localizar elementos gerados por ControlTemplate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 426f6c93433711ac72fe67eff2ee3006aa4d9166
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092099"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Como: localizar elementos gerados por ControlTemplate
Este exemplo mostra como localizar elementos gerados por um <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um estilo que cria um simples <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Button> classe:  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Para localizar um elemento dentro do modelo depois que o modelo foi aplicado, você pode chamar o <xref:System.Windows.FrameworkTemplate.FindName%2A> método da <xref:System.Windows.Controls.Control.Template%2A>. O exemplo a seguir cria uma caixa de mensagem que mostra o valor de largura real do <xref:System.Windows.Controls.Grid> dentro do modelo de controle:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Consulte também

- [Localizar elementos gerados por DataTemplate](../data/how-to-find-datatemplate-generated-elements.md)
- [Estilo e modelagem](styling-and-templating.md)
- [Namescopes XAML WPF](../advanced/wpf-xaml-namescopes.md)
- [Árvores no WPF](../advanced/trees-in-wpf.md)
