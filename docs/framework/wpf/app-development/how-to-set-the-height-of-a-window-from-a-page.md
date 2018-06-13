---
title: 'Como: definir a altura de uma janela de uma página'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: e25bc3cf2f5de01177f79f671390bac39875d079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546049"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Como: definir a altura de uma janela de uma página
Este exemplo ilustra como definir a altura da janela de um <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.Page> pode definir a altura da janela host, definindo <xref:System.Windows.Controls.Page.WindowHeight%2A>. Esta propriedade permite que o <xref:System.Windows.Controls.Page> não tenha conhecimento explícito do tipo de janela que o hospeda.  
  
> [!NOTE]
>  Para definir a altura de uma janela usando <xref:System.Windows.Controls.Page.WindowHeight%2A>, um <xref:System.Windows.Controls.Page> deve ser o filho de uma janela.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
