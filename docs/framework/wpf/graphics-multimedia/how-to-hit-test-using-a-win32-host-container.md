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
ms.openlocfilehash: 01c6a9dad6fccb38be4f240d0900727f776fd2b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560502"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="35aa6-102">Como fazer teste de clique usando um contêiner de host Win32</span><span class="sxs-lookup"><span data-stu-id="35aa6-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="35aa6-103">Você pode criar objetos visuais em um [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] janela fornecendo um host do contêiner de janela para os objetos visuais.</span><span class="sxs-lookup"><span data-stu-id="35aa6-103">You can create visual objects within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="35aa6-104">Para fornecer a manipulação de eventos para os objetos visuais contidos, você processa as mensagens passadas para o loop de filtro de mensagem do contêiner da janela do host.</span><span class="sxs-lookup"><span data-stu-id="35aa6-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="35aa6-105">Consulte [Tutorial: hospedando objetos visuais em um aplicativo Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) para obter mais informações sobre como hospedar objetos visuais em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela.</span><span class="sxs-lookup"><span data-stu-id="35aa6-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35aa6-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35aa6-106">Example</span></span>  
 <span data-ttu-id="35aa6-107">O código a seguir mostra como definir manipuladores de eventos de mouse para um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela que é usada como um contêiner de host para objetos visuais.</span><span class="sxs-lookup"><span data-stu-id="35aa6-107">The following code shows how to set up mouse event handlers for a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="35aa6-108">O exemplo a seguir mostra como configurar um teste de clique em resposta a eventos de mouse específicos de ajuste de registro.</span><span class="sxs-lookup"><span data-stu-id="35aa6-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="35aa6-109">O <xref:System.Windows.Interop.HwndSource> objeto apresenta [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] conteúdo dentro de um [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] janela.</span><span class="sxs-lookup"><span data-stu-id="35aa6-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window.</span></span> <span data-ttu-id="35aa6-110">O valor da <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade o <xref:System.Windows.Interop.HwndSource> objeto representa o nó mais alto na hierarquia de árvore visual.</span><span class="sxs-lookup"><span data-stu-id="35aa6-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="35aa6-111">Para o exemplo completo sobre teste de hit objetos usando um contêiner host Win32, consulte [Hit Test with Win32 interoperação Sample](http://go.microsoft.com/fwlink/?LinkID=159995).</span><span class="sxs-lookup"><span data-stu-id="35aa6-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35aa6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35aa6-112">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="35aa6-113">Teste de clique na camada visual</span><span class="sxs-lookup"><span data-stu-id="35aa6-113">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="35aa6-114">Tutorial: hospedando objetos visuais em um aplicativo Win32</span><span class="sxs-lookup"><span data-stu-id="35aa6-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
