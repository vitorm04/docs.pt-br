---
title: Como remover todos os adornos de um elemento
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
helpviewer_keywords: adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f7bb16c2cd641579706609ff14ca16cc57bd620
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="fa581-102">Como remover todos os adornos de um elemento</span><span class="sxs-lookup"><span data-stu-id="fa581-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="fa581-103">Este exemplo mostra como remover todos os adornos de especificada programaticamente <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="fa581-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa581-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa581-104">Example</span></span>  
 <span data-ttu-id="fa581-105">Este exemplo de código detalhado remove todos os adornos na matriz de adornos retornado por <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa581-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="fa581-106">Este exemplo acontece recupera os adornos em um <xref:System.Windows.UIElement> chamado *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="fa581-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="fa581-107">Se o elemento especificado na chamada para <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> sem adorners, `null` será retornado.</span><span class="sxs-lookup"><span data-stu-id="fa581-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="fa581-108">Esse código verifica explicitamente uma matriz nula e é mais adequado para aplicativos em que se espera uma matriz nula relativamente comum.</span><span class="sxs-lookup"><span data-stu-id="fa581-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="fa581-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa581-109">Example</span></span>  
 <span data-ttu-id="fa581-110">Este exemplo de código condensada é funcionalmente equivalente ao exemplo detalhado mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="fa581-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="fa581-111">Esse código não verifica explicitamente um array nulo, portanto, é possível que um <xref:System.NullReferenceException> exceção poderá ser gerada.</span><span class="sxs-lookup"><span data-stu-id="fa581-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="fa581-112">Esse código é mais adequado para aplicativos em que se espera uma matriz nula rara.</span><span class="sxs-lookup"><span data-stu-id="fa581-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="fa581-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa581-113">See Also</span></span>  
 [<span data-ttu-id="fa581-114">Visão geral de adornos</span><span class="sxs-lookup"><span data-stu-id="fa581-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
