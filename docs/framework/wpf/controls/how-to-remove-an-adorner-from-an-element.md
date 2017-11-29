---
title: Como remover um adorno de um elemento
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
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe11dc8df1a29518ba05792877bd26670f96b29d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="a7d6a-102">Como remover um adorno de um elemento</span><span class="sxs-lookup"><span data-stu-id="a7d6a-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="a7d6a-103">Este exemplo mostra como remover programaticamente um adorno de um <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="a7d6a-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7d6a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7d6a-104">Example</span></span>  
 <span data-ttu-id="a7d6a-105">Este exemplo de código detalhado remove o primeiro adorno na matriz de adornos retornado por <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7d6a-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="a7d6a-106">Este exemplo acontece recupera os adornos em um <xref:System.Windows.UIElement> chamado *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="a7d6a-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="a7d6a-107">Se o elemento especificado na chamada para <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> sem adorners, `null` será retornado.</span><span class="sxs-lookup"><span data-stu-id="a7d6a-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="a7d6a-108">Esse código verifica explicitamente uma matriz nula e é mais adequado para aplicativos em que se espera uma matriz nula relativamente comum.</span><span class="sxs-lookup"><span data-stu-id="a7d6a-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="a7d6a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7d6a-109">Example</span></span>  
 <span data-ttu-id="a7d6a-110">Este exemplo de código condensada é funcionalmente equivalente ao exemplo detalhado mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="a7d6a-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="a7d6a-111">Esse código não verifica explicitamente um array nulo, portanto, é possível que um <xref:System.NullReferenceException> exceção poderá ser gerada.</span><span class="sxs-lookup"><span data-stu-id="a7d6a-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="a7d6a-112">Esse código é mais adequado para aplicativos em que se espera uma matriz nula rara.</span><span class="sxs-lookup"><span data-stu-id="a7d6a-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="a7d6a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7d6a-113">See Also</span></span>  
 [<span data-ttu-id="a7d6a-114">Visão geral de adornos</span><span class="sxs-lookup"><span data-stu-id="a7d6a-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
