---
title: 'Como: determinar se uma página é hospedada pelo navegador'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: c4cb1065807d16c1d1f5a95c8ac9c9cbe5a0fdab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424696"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="b7446-102">Como: determinar se uma página é hospedada pelo navegador</span><span class="sxs-lookup"><span data-stu-id="b7446-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="b7446-103">Este exemplo demonstra como determinar se um <xref:System.Windows.Controls.Page> está hospedado em um navegador.</span><span class="sxs-lookup"><span data-stu-id="b7446-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7446-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7446-104">Example</span></span>  
 <span data-ttu-id="b7446-105">Um <xref:System.Windows.Controls.Page> pode ser independente de host e, consequentemente, pode ser carregado em vários tipos diferentes de hosts, incluindo um <xref:System.Windows.Controls.Frame>, um <xref:System.Windows.Navigation.NavigationWindow>ou um navegador.</span><span class="sxs-lookup"><span data-stu-id="b7446-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="b7446-106">Isso pode acontecer quando você tem um assembly de biblioteca que contém uma ou mais páginas e que é referenciado por vários aplicativos de host autônomos e navegáveis (aplicativo de navegador XAML (XBAP)).</span><span class="sxs-lookup"><span data-stu-id="b7446-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable (XAML browser application (XBAP)) host applications.</span></span>  
  
 <span data-ttu-id="b7446-107">O exemplo a seguir demonstra como usar <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> para determinar se um <xref:System.Windows.Controls.Page> está hospedado em um navegador.</span><span class="sxs-lookup"><span data-stu-id="b7446-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="b7446-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7446-108">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
