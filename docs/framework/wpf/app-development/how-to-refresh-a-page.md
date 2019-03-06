---
title: 'Como: Atualizar uma página'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], refreshing
- refreshing pages [WPF]
ms.assetid: 06dd1bbd-81c4-40ad-ac0d-7a5b326b1465
ms.openlocfilehash: 71a71c91384a8905413358d023531afec23f2d41
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368279"
---
# <a name="how-to-refresh-a-page"></a><span data-ttu-id="e6c8b-102">Como: Atualizar uma página</span><span class="sxs-lookup"><span data-stu-id="e6c8b-102">How to: Refresh a Page</span></span>
<span data-ttu-id="e6c8b-103">Este exemplo mostra como chamar o <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> método para atualizar o conteúdo atual em um <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="e6c8b-103">This example shows how to call the <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> method to refresh the current content in a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6c8b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6c8b-104">Example</span></span>  
 <span data-ttu-id="e6c8b-105"><xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> atualiza o conteúdo atual em um <xref:System.Windows.Navigation.NavigationWindow> a ser recarregado de sua origem.</span><span class="sxs-lookup"><span data-stu-id="e6c8b-105"><xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> refreshes the current content in a <xref:System.Windows.Navigation.NavigationWindow> to be reloaded from its source.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateRefreshCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigaterefreshcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateRefreshCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigaterefreshcode)]
