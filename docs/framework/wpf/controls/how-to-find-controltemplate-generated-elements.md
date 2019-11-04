---
title: Como localizar elementos gerados por ControlTemplate
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 232ee7d2859059591c9beff753f45781598a8127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460710"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Como localizar elementos gerados por ControlTemplate
Este exemplo mostra como localizar elementos que são gerados por um <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um estilo que cria um <xref:System.Windows.Controls.ControlTemplate> simples para a classe <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Para localizar um elemento dentro do modelo após a aplicação do modelo, você pode chamar o método <xref:System.Windows.FrameworkTemplate.FindName%2A> do <xref:System.Windows.Controls.Control.Template%2A>. O exemplo a seguir cria uma caixa de mensagem que mostra o valor de largura real do <xref:System.Windows.Controls.Grid> dentro do modelo de controle:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Consulte também

- [Localizar elementos gerados por DataTemplate](../data/how-to-find-datatemplate-generated-elements.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Namescopes XAML WPF](../advanced/wpf-xaml-namescopes.md)
- [Árvores no WPF](../advanced/trees-in-wpf.md)
