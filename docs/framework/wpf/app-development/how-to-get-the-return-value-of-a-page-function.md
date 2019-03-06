---
title: 'Como: Obter o valor de retorno de uma função da página'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- functions [WPF], getting return values of
- page functions [WPF], getting return values of
- return values of page functions [WPF]
- getting [WPF], return values of page functions
ms.assetid: 75470af6-256c-4c46-87e7-705080723a1c
ms.openlocfilehash: fd54a5059d028f9fc6624d1e2d03b209140b481c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365127"
---
# <a name="how-to-get-the-return-value-of-a-page-function"></a><span data-ttu-id="44bab-102">Como: Obter o valor de retorno de uma função da página</span><span class="sxs-lookup"><span data-stu-id="44bab-102">How to: Get the Return Value of a Page Function</span></span>
<span data-ttu-id="44bab-103">Este exemplo mostra como obter o resultado retornado por uma função de página.</span><span class="sxs-lookup"><span data-stu-id="44bab-103">This example shows how to get the result that is returned by a page function.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44bab-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44bab-104">Example</span></span>  
 <span data-ttu-id="44bab-105">Para obter o resultado é retornado de uma função de página, você precisa tratar <xref:System.Windows.Navigation.PageFunction%601.Return> da função da página que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="44bab-105">To get the result that is returned from a page function, you need to handle <xref:System.Windows.Navigation.PageFunction%601.Return> of the page function you are calling.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#getpagefunctionresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#getpagefunctionresultcodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="44bab-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44bab-106">See also</span></span>
- <xref:System.Windows.Navigation.PageFunction%601>
