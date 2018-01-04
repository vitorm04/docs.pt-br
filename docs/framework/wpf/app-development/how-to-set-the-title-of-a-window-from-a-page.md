---
title: "Como: definir o título de uma janela de uma página"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11f33eede479e090a78bffe841d7998e03eab6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Como: definir o título de uma janela de uma página
Este exemplo mostra como definir o título da janela na qual um <xref:System.Windows.Controls.Page> está hospedado.  
  
## <a name="example"></a>Exemplo  
 Uma página pode alterar o título da janela que está hospedando definindo o <xref:System.Windows.Controls.Page.WindowTitle%2A> propriedade, da seguinte forma:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Definindo o <xref:System.Windows.Controls.Page.Title%2A> propriedade de uma página não altera o valor do título da janela. Em vez disso, <xref:System.Windows.Controls.Page.Title%2A> Especifica o nome da entrada de uma página no histórico de navegação.
