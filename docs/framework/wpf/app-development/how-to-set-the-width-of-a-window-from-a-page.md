---
title: 'Como: definir a largura de uma janela de uma página'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: a0ae0e136e0b7f1cd2a2ec56455e14723e8fa306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Como: definir a largura de uma janela de uma página
Este exemplo ilustra como definir a largura da janela de um <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.Page> pode definir a largura da sua janela de hospedagem definindo <xref:System.Windows.Controls.Page.WindowWidth%2A>. Esta propriedade permite que o <xref:System.Windows.Controls.Page> não tenha conhecimento explícito do tipo de janela que o hospeda.  
  
> [!NOTE]
>  Para definir a largura de uma janela usando <xref:System.Windows.Controls.Page.WindowWidth%2A>, um <xref:System.Windows.Controls.Page> deve ser o filho de uma janela.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
