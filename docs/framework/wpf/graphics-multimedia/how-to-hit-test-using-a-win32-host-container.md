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
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Como fazer teste de clique usando um contêiner de host Win32
Você pode criar objetos visuais em uma janela do Win32 fornecendo um contêiner de janela de host para os objetos visuais. Para fornecer a manipulação de eventos para os objetos visuais contidos, você processa as mensagens passadas para o loop de filtro de mensagem do contêiner da janela do host. Consulte o [tutorial: hospedando objetos visuais em um aplicativo Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) para obter mais informações sobre como hospedar objetos visuais em uma janela do Win32.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como configurar manipuladores de eventos do mouse para uma janela do Win32 que é usada como um contêiner de host para objetos visuais.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 O exemplo a seguir mostra como configurar um teste de clique em resposta a interceptar eventos de mouse específicos.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 O objeto <xref:System.Windows.Interop.HwndSource> apresenta [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] conteúdo em uma janela do Win32. O valor da propriedade <xref:System.Windows.Interop.HwndSource.RootVisual%2A> do objeto <xref:System.Windows.Interop.HwndSource> representa o nó superior na hierarquia da árvore visual.  
  
 Para obter o exemplo completo sobre os objetos de teste de clique usando um contêiner de host do Win32, consulte [teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Interop.HwndSource>
- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
- [Tutorial: hospedando objetos visuais em um aplicativo Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
