---
title: 'Como: Definir o título de uma janela de uma página'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 0f618af89965822b0df96a264997dabd9cae7608
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940780"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Como: Definir o título de uma janela de uma página
Este exemplo mostra como definir o título da janela na qual um <xref:System.Windows.Controls.Page> está hospedado.  
  
## <a name="example"></a>Exemplo  
 Uma página pode alterar o título da janela que a hospeda definindo a <xref:System.Windows.Controls.Page.WindowTitle%2A> Propriedade, desta forma:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
> Definir a <xref:System.Windows.Controls.Page.Title%2A> propriedade de uma página não altera o valor do título da janela. Em vez <xref:System.Windows.Controls.Page.Title%2A> disso, especifica o nome de uma entrada de página no histórico de navegação.
