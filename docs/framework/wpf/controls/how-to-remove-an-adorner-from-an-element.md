---
title: 'Como: Remover um adorno de um elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: 256dd6fa0117f88aec2ef6b60c6dcd4c33b57855
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212395"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="09a9e-102">Como: Remover um adorno de um elemento</span><span class="sxs-lookup"><span data-stu-id="09a9e-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="09a9e-103">Este exemplo mostra como remover um adorno de um de forma programática <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="09a9e-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09a9e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09a9e-104">Example</span></span>  
 <span data-ttu-id="09a9e-105">Este exemplo de código detalhado remove o primeiro adorno na matriz de adornos retornados por <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="09a9e-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="09a9e-106">Este exemplo acontece recupera os adornos em um <xref:System.Windows.UIElement> nomeado *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="09a9e-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="09a9e-107">Se o elemento especificado na chamada para <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> não tiver adornos, `null` será retornado.</span><span class="sxs-lookup"><span data-stu-id="09a9e-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="09a9e-108">Esse código verifica explicitamente uma matriz nula e é mais adequado para aplicativos em que se espera uma matriz nula relativamente comum.</span><span class="sxs-lookup"><span data-stu-id="09a9e-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="09a9e-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09a9e-109">Example</span></span>  
 <span data-ttu-id="09a9e-110">Este exemplo de código condensada é funcionalmente equivalente ao exemplo detalhado mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="09a9e-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="09a9e-111">Esse código não verifica explicitamente uma matriz nula, portanto, é possível que um <xref:System.NullReferenceException> exceção poderá ser gerada.</span><span class="sxs-lookup"><span data-stu-id="09a9e-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="09a9e-112">Esse código é mais adequado para aplicativos em que se espera uma matriz nula rara.</span><span class="sxs-lookup"><span data-stu-id="09a9e-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="09a9e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09a9e-113">See also</span></span>

- [<span data-ttu-id="09a9e-114">Visão geral de adornos</span><span class="sxs-lookup"><span data-stu-id="09a9e-114">Adorners Overview</span></span>](adorners-overview.md)
