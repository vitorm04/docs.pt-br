---
title: "Como chamar uma função de página"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bc72b24b29a43e8aed073600ea863824c93ced6
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="dd898-102">Como chamar uma função de página</span><span class="sxs-lookup"><span data-stu-id="dd898-102">How to: Call a Page Function</span></span>
<span data-ttu-id="dd898-103">Este exemplo mostra como chamar uma função de página de um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] página.</span><span class="sxs-lookup"><span data-stu-id="dd898-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd898-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd898-104">Example</span></span>  
 <span data-ttu-id="dd898-105">Você pode navegar para uma função de página usando um [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], assim como é possível quando você navega para uma página.</span><span class="sxs-lookup"><span data-stu-id="dd898-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="dd898-106">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dd898-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="dd898-107">Se você precisar passar dados para a função de página, você pode criar uma instância dela e passar os dados definindo uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="dd898-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="dd898-108">Ou, como mostra o exemplo a seguir, você pode passar os dados usando um construtor não padrão.</span><span class="sxs-lookup"><span data-stu-id="dd898-108">Or, as the following example shows, you can pass the data using a non-default constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="dd898-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd898-109">See Also</span></span>  
 <xref:System.Windows.Navigation.PageFunction%601>
