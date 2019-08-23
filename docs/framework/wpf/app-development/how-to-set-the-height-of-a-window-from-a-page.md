---
title: 'Como: Definir a altura de uma janela de uma página'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c1041af88241011b51c96d7b61423344a32b25ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940795"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a><span data-ttu-id="8999a-102">Como: Definir a altura de uma janela de uma página</span><span class="sxs-lookup"><span data-stu-id="8999a-102">How to: Set the Height of a Window from a Page</span></span>
<span data-ttu-id="8999a-103">Este exemplo ilustra como definir a altura da janela a partir de um <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="8999a-103">This example illustrates how to set the height of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8999a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8999a-104">Example</span></span>  
 <span data-ttu-id="8999a-105">Um <xref:System.Windows.Controls.Page> pode definir a altura de sua janela de host definindo <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="8999a-105">A <xref:System.Windows.Controls.Page> can set the height of its host window by setting <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span></span> <span data-ttu-id="8999a-106">Essa propriedade permite que <xref:System.Windows.Controls.Page> o não tenha conhecimento explícito do tipo de janela que o hospeda.</span><span class="sxs-lookup"><span data-stu-id="8999a-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8999a-107">Para definir a altura de uma janela usando <xref:System.Windows.Controls.Page.WindowHeight%2A>, um <xref:System.Windows.Controls.Page> deve ser o filho de uma janela.</span><span class="sxs-lookup"><span data-stu-id="8999a-107">To set the height of a window using <xref:System.Windows.Controls.Page.WindowHeight%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
