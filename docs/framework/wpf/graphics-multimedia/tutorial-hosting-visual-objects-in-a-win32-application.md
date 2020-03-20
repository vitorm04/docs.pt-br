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
ms.openlocfilehash: d04357e0770bbf8eebe8f40a86a19ddc9baae3ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187420"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Tutorial: hospedando objetos visuais em um aplicativo Win32
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento substancial no código [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32, pode ser mais eficaz adicionar funcionalidade ao seu aplicativo em vez de reescrever seu código. Para fornecer suporte para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o Win32 e subsistemas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gráficos usados simultaneamente em um aplicativo, fornece um mecanismo para hospedar objetos em uma janela Win32.  
  
 Este tutorial descreve como escrever um aplicativo de exemplo, [Hit Test with Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting), que hospeda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos visuais em uma janela Win32.  

<a name="requirements"></a>
## <a name="requirements"></a>Requisitos  
 Este tutorial assume uma familiaridade [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] básica com a programação do Win32. Para obter uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] introdução básica à programação, consulte [Passo a Passo: Meu primeiro aplicativo de desktop WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Para uma introdução à programação Win32, consulte qualquer um dos inúmeros livros sobre o assunto, em particular *Programação Windows* de Charles Petzold.  
  
> [!NOTE]
> Este tutorial inclui vários exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Para obter o código de amostra completo, consulte [Hit Test com Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="creating_the_host_win32_window"></a>
## <a name="creating-the-host-win32-window"></a>Criando a janela Win32 de host  
 A chave [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para hospedar objetos em <xref:System.Windows.Interop.HwndSource> uma janela Win32 é a classe. Esta classe envolve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os objetos em uma janela Win32, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] permitindo que eles sejam incorporados em sua janela como uma criança.  
  
 O exemplo a seguir mostra <xref:System.Windows.Interop.HwndSource> o código para criar o objeto como a janela do contêiner Win32 para os objetos visuais. Para definir o estilo da janela, a posição e outros <xref:System.Windows.Interop.HwndSourceParameters> parâmetros para a janela Win32, use o objeto.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> O valor <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> da propriedade não pode ser definido como WS_EX_TRANSPARENT. Isso significa que a janela Win32 do host não pode ser transparente. Por essa razão, a cor de fundo da janela win32 do host é definida para a mesma cor de fundo que sua janela pai.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Adicionando objetos visuais na janela do Host Win32  
 Depois de criar uma janela de contêiner Win32 host para os objetos visuais, você pode adicionar objetos visuais a ele. Você vai querer garantir que quaisquer transformações dos objetos visuais, como animações, não se estendam além dos limites do retângulo delimitador da janela Win32 do host.  
  
 O exemplo a seguir mostra <xref:System.Windows.Interop.HwndSource> o código para criar o objeto e adicionar objetos visuais a ele.  
  
> [!NOTE]
> A <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade <xref:System.Windows.Interop.HwndSource> do objeto é definida como o primeiro objeto visual adicionado à janela win32 do host. O objeto visual raiz define o nó mais alto da árvore de objetos visuais. Quaisquer objetos visuais subseqüentes adicionados à janela Win32 do host são adicionados como objetos-filho.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>
## <a name="implementing-the-win32-message-filter"></a>Implementando o filtro de mensagens do Win32  
 A janela host Win32 para os objetos visuais requer um procedimento de filtro de mensagem de janela para lidar com mensagens enviadas para a janela da fila do aplicativo. O procedimento da janela recebe mensagens do sistema Win32. Eles podem ser mensagens de entrada ou de gerenciamento de janela. Opcionalmente, você pode lidar com uma mensagem em seu procedimento de janela ou passar a mensagem para o sistema para processamento padrão.  
  
 O <xref:System.Windows.Interop.HwndSource> objeto que você definiu como pai para os objetos visuais deve fazer referência ao procedimento de filtro de mensagem da janela que você fornece. Quando você <xref:System.Windows.Interop.HwndSource> criar o <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> objeto, defina a propriedade para fazer referência ao procedimento da janela.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 O exemplo a seguir mostra o código para lidar com mensagens com o botões direito e esquerdo do mouse. O valor de coordenada da posição de impacto `lParam` do mouse está contido no valor do parâmetro.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>
## <a name="processing-the-win32-messages"></a>Processando as mensagens do Win32  
 O código no exemplo a seguir mostra como um teste de hit é realizado contra a hierarquia de objetos visuais contidos na janela Win32 do host. Você pode identificar se um ponto está dentro da geometria de um objeto visual, usando o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método para especificar o objeto visual raiz e o valor de coordenada para testar. Neste caso, o objeto visual raiz <xref:System.Windows.Interop.HwndSource.RootVisual%2A> é o <xref:System.Windows.Interop.HwndSource> valor da propriedade do objeto.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Para obter mais informações sobre testes de acerto contra objetos visuais, consulte [Teste de hit na camada visual](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Interop.HwndSource>
- [Exemplo de teste de clique com interoperação do Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
