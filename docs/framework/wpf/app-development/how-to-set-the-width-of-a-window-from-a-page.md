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
ms.openlocfilehash: 7354a6c3f1b913494da9ad45181a0c7741a1cfa2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Como: definir a largura de uma janela de uma página
Este exemplo ilustra como definir a largura da janela de um <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.Page> pode definir a largura da sua janela de hospedagem definindo <xref:System.Windows.Controls.Page.WindowWidth%2A>. Esta propriedade permite que o <xref:System.Windows.Controls.Page> não tenha conhecimento explícito do tipo de janela que o hospeda.  
  
> [!NOTE]
>  Para definir a largura de uma janela usando <xref:System.Windows.Controls.Page.WindowWidth%2A>, um <xref:System.Windows.Controls.Page> deve ser o filho de uma janela.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
