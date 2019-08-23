---
title: 'Tutorial: Hospedar objetos visuais em um aplicativo Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: c8baefbf01467a65626a77f300f34a145d5c7281
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962868"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Tutorial: Hospedar objetos visuais em um aplicativo Win32
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] substancial em código, pode ser mais eficiente adicionar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funcionalidade ao seu aplicativo em vez de reescrever seu código. Para fornecer suporte para [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] subsistemas gráficos usados simultaneamente em um aplicativo, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o fornece um mecanismo para hospedar objetos em uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela.  
  
 Este tutorial descreve como escrever um aplicativo de exemplo, um [teste de clique com o exemplo](https://go.microsoft.com/fwlink/?LinkID=159995)de interoperação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do Win32, que [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hospeda objetos visuais em uma janela.  

<a name="requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Este tutorial pressupõe uma familiaridade básica com ambos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programação. Para obter uma introdução básica [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à programação, [consulte Walkthrough: Meu primeiro aplicativo](../getting-started/walkthrough-my-first-wpf-desktop-application.md)de área de trabalho do WPF. Para obter uma introdução [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] à programação, consulte qualquer um dos vários livros sobre o assunto, em particular, as *janelas de programação* , de Charles Petzold.  
  
> [!NOTE]
> Este tutorial inclui vários exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Para obter o código de exemplo completo, consulte [teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Criando a janela Win32 de host  
 A chave para hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos em uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela é a <xref:System.Windows.Interop.HwndSource> classe. Essa classe encapsula os [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos em uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela, permitindo que eles sejam incorporados em seu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] como uma janela filho.  
  
 O exemplo a seguir mostra o código para criar <xref:System.Windows.Interop.HwndSource> o objeto como [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a janela de contêiner para os objetos visuais. Para definir o estilo de janela, a posição e outros parâmetros para [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a janela, use <xref:System.Windows.Interop.HwndSourceParameters> o objeto.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> O valor da <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> propriedade não pode ser definido como WS_EX_TRANSPARENT. Isso significa que a janela [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] do host não pode ser transparente. Por esse motivo, a cor do plano de fundo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] da janela do host é definida como a mesma cor de plano de fundo da janela pai.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Adicionando objetos visuais na janela do Host Win32  
 Depois de criar uma janela de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contêiner de host para os objetos visuais, você pode adicionar objetos visuais a ele. Você desejará garantir que todas as transformações dos objetos visuais, como animações, não ultrapassem os limites do retângulo delimitador da [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela do host.  
  
 O exemplo a seguir mostra o código para criar <xref:System.Windows.Interop.HwndSource> o objeto e adicionar objetos visuais a ele.  
  
> [!NOTE]
> A <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] do objeto é definida como o primeiro objeto visual adicionado à janela do host. <xref:System.Windows.Interop.HwndSource> O objeto visual raiz define o nó mais alto da árvore de objetos visuais. Todos os objetos visuais subsequentes adicionados à [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela do host são adicionados como objetos filho.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementando o filtro de mensagens do Win32  
 A janela [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] host para os objetos visuais requer um procedimento de filtro de mensagem de janela para manipular as mensagens que são enviadas para a janela da fila do aplicativo. O procedimento de janela recebe mensagens do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sistema. Eles podem ser mensagens de entrada ou de gerenciamento de janela. Opcionalmente, você pode lidar com uma mensagem em seu procedimento de janela ou passar a mensagem para o sistema para processamento padrão.  
  
 O <xref:System.Windows.Interop.HwndSource> objeto que você definiu como pai para os objetos visuais deve fazer referência ao procedimento de filtro de mensagem de janela que você fornecer. Ao criar o <xref:System.Windows.Interop.HwndSource> objeto, defina a <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> propriedade para fazer referência ao procedimento de janela.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 O exemplo a seguir mostra o código para lidar com mensagens com o botões direito e esquerdo do mouse. O valor da coordenada da posição de pressionamento do mouse está contido no `lParam` valor do parâmetro.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Processando as mensagens do Win32  
 O código no exemplo a seguir mostra como um teste de clique é executado em relação à hierarquia de objetos visuais contidos na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela do host. Você pode identificar se um ponto está dentro da geometria de um objeto visual, usando o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método para especificar o objeto visual raiz e o valor da coordenada para o teste de clique em relação a. Nesse caso, o objeto visual raiz é o valor da <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade <xref:System.Windows.Interop.HwndSource> do objeto.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Para obter mais informações sobre testes de clique em objetos visuais, consulte [teste de clique na camada Visual](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Interop.HwndSource>
- [Teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
