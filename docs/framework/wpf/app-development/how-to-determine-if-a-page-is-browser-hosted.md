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
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Como: determinar se uma página é hospedada pelo navegador
Este exemplo demonstra como determinar se um <xref:System.Windows.Controls.Page> está hospedado em um navegador.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.Page> pode ser independente de host e, consequentemente, pode ser carregado em vários tipos diferentes de hosts, incluindo um <xref:System.Windows.Controls.Frame>, um <xref:System.Windows.Navigation.NavigationWindow>ou um navegador. Isso pode acontecer quando você tem um assembly de biblioteca que contém uma ou mais páginas e que é referenciado por vários aplicativos de host autônomos e navegáveis (aplicativo de navegador XAML (XBAP)).  
  
 O exemplo a seguir demonstra como usar <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> para determinar se um <xref:System.Windows.Controls.Page> está hospedado em um navegador.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
