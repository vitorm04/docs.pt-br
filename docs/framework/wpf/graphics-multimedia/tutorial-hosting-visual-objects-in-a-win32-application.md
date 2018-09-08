---
title: 'Tutorial: hospedando objetos visuais em um aplicativo Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: 4db60418512080d6bf13ef00b1c6e7dce797a16b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192984"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Tutorial: hospedando objetos visuais em um aplicativo Win32
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento substancial em [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] código, ele pode ser mais eficiente adicionar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funcionalidade ao seu aplicativo em vez de reescrever o código. Para fornecer suporte para [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] subsistemas de elementos gráficos usados simultaneamente em um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece um mecanismo para hospedar objetos em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela.  
  
 Este tutorial descreve como escrever um aplicativo de exemplo [teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995), que hosts [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos visuais em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela.  
  

  
<a name="requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Este tutorial pressupõe uma familiaridade básica com ambos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de programação. Para obter uma introdução básica [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de programação, consulte [passo a passo: meu primeiro aplicativo da área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Para obter uma introdução [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de programação, consulte qualquer um dos vários livros sobre o assunto, em particular *Programming Windows* por Charles Petzold.  
  
> [!NOTE]
>  Este tutorial inclui vários exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Para o código de exemplo completo, consulte [teste de clique com o exemplo de interoperação Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Criando a janela Win32 de host  
 A chave para hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela é o <xref:System.Windows.Interop.HwndSource> classe. Essa classe encapsula o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela, permitindo que eles sejam incorporados em seu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] como uma janela filho.  
  
 O exemplo a seguir mostra o código para criar o <xref:System.Windows.Interop.HwndSource> objeto como o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela de contêiner para os objetos visuais. Para definir o estilo da janela, posição e outros parâmetros para o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela, use o <xref:System.Windows.Interop.HwndSourceParameters> objeto.  
  
 [!code-csharp[VisualsHitTesting#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  O valor da <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> propriedade não pode ser definida como WS_EX_TRANSPARENT. Isso significa que o host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela não pode ser transparente. Por esse motivo, a cor do plano de fundo do host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela é definida como a mesma cor do plano de fundo de sua janela pai.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Adicionando objetos visuais na janela do Host Win32  
 Depois de criar um host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela de contêiner para os objetos visuais, você pode adicionar objetos visuais a ele. Você desejará garantir que todas as transformações dos objetos visuais, como animações, não se estendem além dos limites do host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela do retângulo delimitador.  
  
 O exemplo a seguir mostra o código para criar o <xref:System.Windows.Interop.HwndSource> do objeto e adicionar objetos visuais a ele.  
  
> [!NOTE]
>  O <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade do <xref:System.Windows.Interop.HwndSource> objeto é definido como o primeiro objeto visual adicionado ao host de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela. O objeto visual raiz define o nó mais alto da árvore de objetos visuais. Quaisquer objetos visuais subsequentes adicionados ao host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela são adicionados como objetos filho.  
  
 [!code-csharp[VisualsHitTesting#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementando o filtro de mensagens do Win32  
 O host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela para os objetos visuais exige um procedimento de filtro de mensagem de janela para lidar com mensagens enviadas para a janela da fila de aplicativos. O procedimento de janela recebe mensagens do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sistema. Eles podem ser mensagens de entrada ou de gerenciamento de janela. Opcionalmente, você pode lidar com uma mensagem em seu procedimento de janela ou passar a mensagem para o sistema para processamento padrão.  
  
 O <xref:System.Windows.Interop.HwndSource> objeto definido como pai para os objetos visuais deve referenciar o procedimento de filtro de mensagem de janela você fornecer. Quando você cria o <xref:System.Windows.Interop.HwndSource> do objeto, defina o <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> propriedade a referenciar o procedimento de janela.  
  
 [!code-csharp[VisualsHitTesting#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 O exemplo a seguir mostra o código para lidar com mensagens com o botões direito e esquerdo do mouse. Posição de atingir o valor da coordenada do mouse está contido no valor da `lParam` parâmetro.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Processando as mensagens do Win32  
 O código no exemplo a seguir mostra como um teste de clique é executado em relação a hierarquia de objetos visuais contidos no host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela. Você pode identificar se um ponto está dentro da geometria de um objeto visual, usando o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método para especificar o objeto visual raiz e o valor da coordenada para teste de clique em. Nesse caso, o objeto visual raiz é o valor da <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade do <xref:System.Windows.Interop.HwndSource> objeto.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Para obter mais informações sobre teste de clique em objetos visuais, consulte [teste de clique na camada Visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Interop.HwndSource>  
 [Teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995)  
 [Teste de clique na camada visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
