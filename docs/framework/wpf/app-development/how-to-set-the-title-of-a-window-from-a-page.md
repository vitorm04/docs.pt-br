---
title: 'Como: Definir o título de uma janela de uma página'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 55444de6c61107979307b94910ba944e7001cf9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053997"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Como: Definir o título de uma janela de uma página
Este exemplo mostra como definir o título da janela na qual um <xref:System.Windows.Controls.Page> está hospedado.  
  
## <a name="example"></a>Exemplo  
 Uma página pode alterar o título da janela que está hospedando, definindo o <xref:System.Windows.Controls.Page.WindowTitle%2A> propriedade, da seguinte forma:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Definindo o <xref:System.Windows.Controls.Page.Title%2A> propriedade de uma página não altera o valor do título da janela. Em vez disso, <xref:System.Windows.Controls.Page.Title%2A> Especifica o nome da entrada de uma página no histórico de navegação.
