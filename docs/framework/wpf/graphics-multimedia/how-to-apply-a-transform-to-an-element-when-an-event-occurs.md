---
title: Como aplicar uma transformação a um elemento quando ocorre um evento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: bd50b369666a1b65226b2b7eb6f3d866ec670bde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558971"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="94384-102">Como aplicar uma transformação a um elemento quando ocorre um evento</span><span class="sxs-lookup"><span data-stu-id="94384-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="94384-103">Este exemplo mostra como aplicar uma <xref:System.Windows.Media.ScaleTransform> quando ocorre um evento.</span><span class="sxs-lookup"><span data-stu-id="94384-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="94384-104">O conceito que é mostrado aqui é o mesmo que você usa para aplicar outros tipos de transformações.</span><span class="sxs-lookup"><span data-stu-id="94384-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="94384-105">Para obter mais informações sobre os tipos disponíveis de transformações, consulte o <xref:System.Windows.Media.Transform> classe ou [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="94384-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
 <span data-ttu-id="94384-106">Você pode aplicar uma transformação a um elemento de uma destas duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="94384-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
-   <span data-ttu-id="94384-107">Se você fizer *não* deseja que a transformação para afetar o layout, use o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade do elemento.</span><span class="sxs-lookup"><span data-stu-id="94384-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
-   <span data-ttu-id="94384-108">Se você quiser que a transformação afete o layout, use o <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriedade do elemento.</span><span class="sxs-lookup"><span data-stu-id="94384-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="94384-109">O exemplo a seguir aplica-se um <xref:System.Windows.Media.ScaleTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de um botão.</span><span class="sxs-lookup"><span data-stu-id="94384-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="94384-110">Quando o mouse se move sobre o botão, o <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedades do <xref:System.Windows.Media.ScaleTransform> são definidos como `2`, que faz com que o botão fique maior.</span><span class="sxs-lookup"><span data-stu-id="94384-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="94384-111">Quando o mouse é movido para fora do botão <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> são definidos como `1`, que faz com que o botão para retornar ao seu tamanho original.</span><span class="sxs-lookup"><span data-stu-id="94384-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94384-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94384-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="94384-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94384-113">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="94384-114">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="94384-114">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="94384-115">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="94384-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="94384-116">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="94384-116">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
