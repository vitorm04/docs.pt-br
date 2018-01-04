---
title: "Como: definir a largura de uma janela de uma página"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc9843d4a0f76547b76698a9686b5c4936baa322
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Como: definir a largura de uma janela de uma página
Este exemplo ilustra como definir a largura da janela de um <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.Page> pode definir a largura da sua janela de hospedagem definindo <xref:System.Windows.Controls.Page.WindowWidth%2A>. Esta propriedade permite que o <xref:System.Windows.Controls.Page> não tenha conhecimento explícito do tipo de janela que o hospeda.  
  
> [!NOTE]
>  Para definir a largura de uma janela usando <xref:System.Windows.Controls.Page.WindowWidth%2A>, um <xref:System.Windows.Controls.Page> deve ser o filho de uma janela.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
