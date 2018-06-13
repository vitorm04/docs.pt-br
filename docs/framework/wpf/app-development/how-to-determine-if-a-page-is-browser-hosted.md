---
title: 'Como: determinar se uma página está hospedada no navegador'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: 6eb83429cb4f9dac5f3561b41997d24bcaa2c62f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545871"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="e8e9a-102">Como: determinar se uma página está hospedada no navegador</span><span class="sxs-lookup"><span data-stu-id="e8e9a-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="e8e9a-103">Este exemplo demonstra como determinar se um <xref:System.Windows.Controls.Page> está hospedado em um navegador.</span><span class="sxs-lookup"><span data-stu-id="e8e9a-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8e9a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8e9a-104">Example</span></span>  
 <span data-ttu-id="e8e9a-105">Um <xref:System.Windows.Controls.Page> pode ser independente de host e, consequentemente, pode ser carregado em vários tipos diferentes de hosts, incluindo uma <xref:System.Windows.Controls.Frame>, um <xref:System.Windows.Navigation.NavigationWindow>, ou um navegador.</span><span class="sxs-lookup"><span data-stu-id="e8e9a-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="e8e9a-106">Isso pode acontecer quando você tem um assembly de biblioteca que contém uma ou mais páginas, e que é referenciado por várias autônomo e navegável ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) hospedar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e8e9a-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) host applications.</span></span>  
  
 <span data-ttu-id="e8e9a-107">O exemplo a seguir demonstra como usar <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> para determinar se um <xref:System.Windows.Controls.Page> está hospedado em um navegador.</span><span class="sxs-lookup"><span data-stu-id="e8e9a-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="e8e9a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8e9a-108">See Also</span></span>  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
