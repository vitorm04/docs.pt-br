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
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661706"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Como fazer teste de clique usando um contêiner de host Win32
Você pode criar objetos visuais em um [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] janela, fornecendo um host do contêiner de janela para os objetos visuais. Para fornecer a manipulação de eventos para os objetos visuais contidos, você processa as mensagens passadas para o loop de filtro de mensagem do contêiner da janela do host. Consulte a [Tutorial: hospedando objetos visuais em um aplicativo Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) para obter mais informações sobre como hospedar objetos visuais em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como definir manipuladores de eventos de mouse para um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela que é usada como um contêiner hospedeiro para objetos visuais.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 O exemplo a seguir mostra como configurar um teste de clique em resposta a eventos de mouse específicos de trapping.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 O <xref:System.Windows.Interop.HwndSource> objeto apresenta [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] conteúdo dentro de um [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] janela. O valor da <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade do <xref:System.Windows.Interop.HwndSource> objeto representa o nó mais alto na hierarquia da árvore visual.  
  
 Para obter o exemplo completo sobre teste de clique objetos usando um contêiner de host Win32, consulte [teste de clique com o exemplo de interoperação Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Interop.HwndSource>  
 [Teste de clique na camada visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Tutorial: hospedando objetos visuais em um aplicativo Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
