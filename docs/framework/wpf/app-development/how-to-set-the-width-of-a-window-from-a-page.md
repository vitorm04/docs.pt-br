---
title: 'Como: Definir a largura de uma janela de uma página'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: fee6d4c9ae9dae03e81cc4be56576763cb59958b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379348"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Como: Definir a largura de uma janela de uma página
Este exemplo ilustra como definir a largura da janela a partir um <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.Page> pode definir a largura da sua janela de host definindo <xref:System.Windows.Controls.Page.WindowWidth%2A>. Essa propriedade permite que o <xref:System.Windows.Controls.Page> não ter conhecimento explícito sobre o tipo de janela que o hospeda.  
  
> [!NOTE]
>  Para definir a largura de uma janela usando <xref:System.Windows.Controls.Page.WindowWidth%2A>, um <xref:System.Windows.Controls.Page> deve ser o filho de uma janela.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
