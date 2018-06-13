---
title: 'Como: definir o título de uma janela de uma página'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: e69812b59783717b7b9c832d4e8ab01ab42827c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546179"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Como: definir o título de uma janela de uma página
Este exemplo mostra como definir o título da janela na qual um <xref:System.Windows.Controls.Page> está hospedado.  
  
## <a name="example"></a>Exemplo  
 Uma página pode alterar o título da janela que está hospedando definindo o <xref:System.Windows.Controls.Page.WindowTitle%2A> propriedade, da seguinte forma:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Definindo o <xref:System.Windows.Controls.Page.Title%2A> propriedade de uma página não altera o valor do título da janela. Em vez disso, <xref:System.Windows.Controls.Page.Title%2A> Especifica o nome da entrada de uma página no histórico de navegação.
