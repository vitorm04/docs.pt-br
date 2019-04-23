---
title: 'Como: Determinar se uma página está hospedada no navegador'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: d154de2f885101d1bd0c4613dfb1604be8acbe6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978335"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Como: Determinar se uma página está hospedada no navegador
Este exemplo demonstra como determinar se um <xref:System.Windows.Controls.Page> está hospedado em um navegador.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.Page> pode ser independente de host e, consequentemente, pode ser carregado em vários tipos diferentes de hosts, incluindo uma <xref:System.Windows.Controls.Frame>, um <xref:System.Windows.Navigation.NavigationWindow>, ou um navegador. Isso pode acontecer quando você tem um assembly de biblioteca que contém uma ou mais páginas, e que é referenciado por várias autônomo e navegável ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) hospedar aplicativos.  
  
 O exemplo a seguir demonstra como usar <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> para determinar se um <xref:System.Windows.Controls.Page> está hospedado em um navegador.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
