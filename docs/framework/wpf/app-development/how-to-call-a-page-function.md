---
title: 'Como: Chamar uma função de página'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
ms.openlocfilehash: e7c7c5ef98feeb4c5557295d92a8b219d9799865
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364157"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="2aa82-102">Como: Chamar uma função de página</span><span class="sxs-lookup"><span data-stu-id="2aa82-102">How to: Call a Page Function</span></span>
<span data-ttu-id="2aa82-103">Este exemplo mostra como chamar uma função de página de uma [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] página.</span><span class="sxs-lookup"><span data-stu-id="2aa82-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aa82-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2aa82-104">Example</span></span>  
 <span data-ttu-id="2aa82-105">Você pode navegar para uma função de página usando [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]uma, assim como você pode quando navega para uma página.</span><span class="sxs-lookup"><span data-stu-id="2aa82-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="2aa82-106">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2aa82-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="2aa82-107">Se você precisar passar dados para a função Page, poderá criar uma instância dele e passar os dados definindo uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="2aa82-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="2aa82-108">Ou, como mostra o exemplo a seguir, você pode passar os dados usando um construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2aa82-108">Or, as the following example shows, you can pass the data using a non-parameterless constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="2aa82-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2aa82-109">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
