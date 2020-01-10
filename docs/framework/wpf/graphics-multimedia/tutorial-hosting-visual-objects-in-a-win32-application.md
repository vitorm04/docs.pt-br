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
ms.openlocfilehash: 621684e14f9d1b599c4ef60e3731f0f58f31aacd
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740168"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Tutorial: hospedando objetos visuais em um aplicativo Win32
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento substancial no código Win32, pode ser mais eficiente adicionar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funcionalidade ao seu aplicativo em vez de reescrever seu código. Para fornecer suporte para os subsistemas de gráficos do Win32 e do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usados simultaneamente em um aplicativo, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece um mecanismo para hospedar objetos em uma janela do Win32.  
  
 Este tutorial descreve como escrever um aplicativo de exemplo, um [teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995), que hospeda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos visuais em uma janela do Win32.  

<a name="requirements"></a>   
## <a name="requirements"></a>Requisitos do  
 Este tutorial pressupõe uma familiaridade básica com a programação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e Win32. Para obter uma introdução básica à programação de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], confira [Walkthrough: meu primeiro aplicativo de área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Para obter uma introdução à programação do Win32, confira qualquer um dos vários livros sobre o assunto, em particular, as *janelas de programação* de Charles Petzold.  
  
> [!NOTE]
> Este tutorial inclui vários exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Para obter o código de exemplo completo, consulte [teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Criando a janela Win32 de host  
 A chave para hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos em uma janela do Win32 é a classe <xref:System.Windows.Interop.HwndSource>. Essa classe encapsula os objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela do Win32, permitindo que eles sejam incorporados ao seu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] como uma janela filho.  
  
 O exemplo a seguir mostra o código para criar o objeto <xref:System.Windows.Interop.HwndSource> como a janela contêiner do Win32 para os objetos visuais. Para definir o estilo de janela, a posição e outros parâmetros para a janela do Win32, use o objeto <xref:System.Windows.Interop.HwndSourceParameters>.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> O valor da propriedade <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> não pode ser definido como WS_EX_TRANSPARENT. Isso significa que a janela host do Win32 não pode ser transparente. Por esse motivo, a cor do plano de fundo da janela do host do Win32 é definida como a mesma cor de plano de fundo da janela pai.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Adicionando objetos visuais na janela do Host Win32  
 Depois de criar uma janela de contêiner do Win32 de host para os objetos visuais, você pode adicionar objetos visuais a ele. Você desejará garantir que todas as transformações dos objetos visuais, como animações, não ultrapassem os limites do retângulo delimitador da janela do host do Win32.  
  
 O exemplo a seguir mostra o código para criar o objeto <xref:System.Windows.Interop.HwndSource> e adicionar objetos visuais a ele.  
  
> [!NOTE]
> A propriedade <xref:System.Windows.Interop.HwndSource.RootVisual%2A> do objeto <xref:System.Windows.Interop.HwndSource> é definida como o primeiro objeto visual adicionado à janela do host do Win32. O objeto visual raiz define o nó mais alto da árvore de objetos visuais. Todos os objetos visuais subsequentes adicionados à janela do host do Win32 são adicionados como objetos filho.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementando o filtro de mensagens do Win32  
 A janela do host do Win32 para os objetos visuais requer um procedimento de filtro de mensagem de janela para manipular as mensagens que são enviadas para a janela da fila do aplicativo. O procedimento de janela recebe mensagens do sistema Win32. Eles podem ser mensagens de entrada ou de gerenciamento de janela. Opcionalmente, você pode lidar com uma mensagem em seu procedimento de janela ou passar a mensagem para o sistema para processamento padrão.  
  
 O objeto <xref:System.Windows.Interop.HwndSource> que você definiu como pai para os objetos visuais deve fazer referência ao procedimento de filtro de mensagem de janela que você fornecer. Ao criar o objeto <xref:System.Windows.Interop.HwndSource>, defina a propriedade <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> para fazer referência ao procedimento de janela.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 O exemplo a seguir mostra o código para lidar com mensagens com o botões direito e esquerdo do mouse. O valor da coordenada da posição de pressionamento do mouse está contido no valor do parâmetro `lParam`.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Processando as mensagens do Win32  
 O código no exemplo a seguir mostra como um teste de clique é executado em relação à hierarquia de objetos visuais contidos na janela do host do Win32. Você pode identificar se um ponto está dentro da geometria de um objeto visual, usando o método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> para especificar o objeto visual raiz e o valor da coordenada para o teste de clique em relação a. Nesse caso, o objeto visual raiz é o valor da propriedade <xref:System.Windows.Interop.HwndSource.RootVisual%2A> do objeto <xref:System.Windows.Interop.HwndSource>.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Para obter mais informações sobre testes de clique em objetos visuais, consulte [teste de clique na camada Visual](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Interop.HwndSource>
- [Teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
