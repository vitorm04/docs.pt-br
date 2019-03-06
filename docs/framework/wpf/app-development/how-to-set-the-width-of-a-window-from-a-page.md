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
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="eeb9f-102">Como: Definir a largura de uma janela de uma página</span><span class="sxs-lookup"><span data-stu-id="eeb9f-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="eeb9f-103">Este exemplo ilustra como definir a largura da janela a partir um <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="eeb9f-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eeb9f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eeb9f-104">Example</span></span>  
 <span data-ttu-id="eeb9f-105">Um <xref:System.Windows.Controls.Page> pode definir a largura da sua janela de host definindo <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span><span class="sxs-lookup"><span data-stu-id="eeb9f-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="eeb9f-106">Essa propriedade permite que o <xref:System.Windows.Controls.Page> não ter conhecimento explícito sobre o tipo de janela que o hospeda.</span><span class="sxs-lookup"><span data-stu-id="eeb9f-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eeb9f-107">Para definir a largura de uma janela usando <xref:System.Windows.Controls.Page.WindowWidth%2A>, um <xref:System.Windows.Controls.Page> deve ser o filho de uma janela.</span><span class="sxs-lookup"><span data-stu-id="eeb9f-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
