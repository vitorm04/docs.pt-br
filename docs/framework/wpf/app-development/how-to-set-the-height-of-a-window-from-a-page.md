---
title: 'Como: Definir a altura de uma janela de uma página'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c99ea134478635f368b71443f43e4d8f772cb5aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007289"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Como: Definir a altura de uma janela de uma página
Este exemplo ilustra como definir a altura da janela a partir um <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.Page> pode definir a altura da sua janela de host definindo <xref:System.Windows.Controls.Page.WindowHeight%2A>. Essa propriedade permite que o <xref:System.Windows.Controls.Page> não ter conhecimento explícito sobre o tipo de janela que o hospeda.  
  
> [!NOTE]
>  Para definir a altura de uma janela usando <xref:System.Windows.Controls.Page.WindowHeight%2A>, um <xref:System.Windows.Controls.Page> deve ser o filho de uma janela.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
