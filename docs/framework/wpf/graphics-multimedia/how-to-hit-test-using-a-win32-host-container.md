---
title: Como fazer teste de clique usando um contêiner de host Win32
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: b71783f2d061c9139de4449d8e0106eb00345894
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740181"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="2f0f9-102">Como fazer teste de clique usando um contêiner de host Win32</span><span class="sxs-lookup"><span data-stu-id="2f0f9-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="2f0f9-103">Você pode criar objetos visuais em uma janela do Win32 fornecendo um contêiner de janela de host para os objetos visuais.</span><span class="sxs-lookup"><span data-stu-id="2f0f9-103">You can create visual objects within a Win32 window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="2f0f9-104">Para fornecer a manipulação de eventos para os objetos visuais contidos, você processa as mensagens passadas para o loop de filtro de mensagem do contêiner da janela do host.</span><span class="sxs-lookup"><span data-stu-id="2f0f9-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="2f0f9-105">Consulte o [tutorial: hospedando objetos visuais em um aplicativo Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) para obter mais informações sobre como hospedar objetos visuais em uma janela do Win32.</span><span class="sxs-lookup"><span data-stu-id="2f0f9-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a Win32 window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f0f9-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f0f9-106">Example</span></span>  
 <span data-ttu-id="2f0f9-107">O código a seguir mostra como configurar manipuladores de eventos do mouse para uma janela do Win32 que é usada como um contêiner de host para objetos visuais.</span><span class="sxs-lookup"><span data-stu-id="2f0f9-107">The following code shows how to set up mouse event handlers for a Win32 window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="2f0f9-108">O exemplo a seguir mostra como configurar um teste de clique em resposta a interceptar eventos de mouse específicos.</span><span class="sxs-lookup"><span data-stu-id="2f0f9-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="2f0f9-109">O objeto <xref:System.Windows.Interop.HwndSource> apresenta [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] conteúdo em uma janela do Win32.</span><span class="sxs-lookup"><span data-stu-id="2f0f9-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a Win32 window.</span></span> <span data-ttu-id="2f0f9-110">O valor da propriedade <xref:System.Windows.Interop.HwndSource.RootVisual%2A> do objeto <xref:System.Windows.Interop.HwndSource> representa o nó superior na hierarquia da árvore visual.</span><span class="sxs-lookup"><span data-stu-id="2f0f9-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="2f0f9-111">Para obter o exemplo completo sobre os objetos de teste de clique usando um contêiner de host do Win32, consulte [teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995).</span><span class="sxs-lookup"><span data-stu-id="2f0f9-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0f9-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="2f0f9-112">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="2f0f9-113">Teste de clique na camada visual</span><span class="sxs-lookup"><span data-stu-id="2f0f9-113">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="2f0f9-114">Tutorial: hospedando objetos visuais em um aplicativo Win32</span><span class="sxs-lookup"><span data-stu-id="2f0f9-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](tutorial-hosting-visual-objects-in-a-win32-application.md)
