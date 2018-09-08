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
ms.openlocfilehash: bb175e0f8aeb126b7f7fa85d5af1c4afcf5bea61
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44212380"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="edf28-102">Como fazer teste de clique usando um contêiner de host Win32</span><span class="sxs-lookup"><span data-stu-id="edf28-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="edf28-103">Você pode criar objetos visuais em um [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] janela, fornecendo um host do contêiner de janela para os objetos visuais.</span><span class="sxs-lookup"><span data-stu-id="edf28-103">You can create visual objects within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="edf28-104">Para fornecer a manipulação de eventos para os objetos visuais contidos, você processa as mensagens passadas para o loop de filtro de mensagem do contêiner da janela do host.</span><span class="sxs-lookup"><span data-stu-id="edf28-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="edf28-105">Consulte a [Tutorial: hospedando objetos visuais em um aplicativo Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) para obter mais informações sobre como hospedar objetos visuais em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela.</span><span class="sxs-lookup"><span data-stu-id="edf28-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edf28-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="edf28-106">Example</span></span>  
 <span data-ttu-id="edf28-107">O código a seguir mostra como definir manipuladores de eventos de mouse para um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela que é usada como um contêiner hospedeiro para objetos visuais.</span><span class="sxs-lookup"><span data-stu-id="edf28-107">The following code shows how to set up mouse event handlers for a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="edf28-108">O exemplo a seguir mostra como configurar um teste de clique em resposta a eventos de mouse específicos de trapping.</span><span class="sxs-lookup"><span data-stu-id="edf28-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="edf28-109">O <xref:System.Windows.Interop.HwndSource> objeto apresenta [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] conteúdo dentro de um [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] janela.</span><span class="sxs-lookup"><span data-stu-id="edf28-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window.</span></span> <span data-ttu-id="edf28-110">O valor da <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade do <xref:System.Windows.Interop.HwndSource> objeto representa o nó mais alto na hierarquia da árvore visual.</span><span class="sxs-lookup"><span data-stu-id="edf28-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="edf28-111">Para obter o exemplo completo sobre teste de clique objetos usando um contêiner de host Win32, consulte [teste de clique com o exemplo de interoperação Win32](https://go.microsoft.com/fwlink/?LinkID=159995).</span><span class="sxs-lookup"><span data-stu-id="edf28-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf28-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edf28-112">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="edf28-113">Teste de clique na camada visual</span><span class="sxs-lookup"><span data-stu-id="edf28-113">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="edf28-114">Tutorial: hospedando objetos visuais em um aplicativo Win32</span><span class="sxs-lookup"><span data-stu-id="edf28-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
