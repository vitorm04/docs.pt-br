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
ms.openlocfilehash: fb58d50a63cca41420aa102ca0c8b63f3b14c0d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980181"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="56d10-102">Como: Chamar uma função de página</span><span class="sxs-lookup"><span data-stu-id="56d10-102">How to: Call a Page Function</span></span>
<span data-ttu-id="56d10-103">Este exemplo mostra como chamar uma função de página de um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] página.</span><span class="sxs-lookup"><span data-stu-id="56d10-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56d10-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56d10-104">Example</span></span>  
 <span data-ttu-id="56d10-105">Você pode navegar para uma função de página usando um [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], exatamente como é possível quando você navega para uma página.</span><span class="sxs-lookup"><span data-stu-id="56d10-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="56d10-106">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="56d10-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="56d10-107">Se você precisar passar dados para a função de página, você pode criar uma instância dela e passar os dados ao definir uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="56d10-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="56d10-108">Ou, como mostra o exemplo a seguir, você pode passar os dados usando um construtor não padrão.</span><span class="sxs-lookup"><span data-stu-id="56d10-108">Or, as the following example shows, you can pass the data using a non-default constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="56d10-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56d10-109">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
