---
title: Compartilhando loops de mensagem entre Win32 e WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 5c1d75ab9598196e9cffc78a2f116993e722fd38
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740321"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Compartilhando loops de mensagem entre Win32 e WPF
Este tópico descreve como implementar um loop de mensagem para interoperação com [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], usando a exposição de loop de mensagem existente no <xref:System.Windows.Threading.Dispatcher> ou criando um loop de mensagem separado no lado do Win32 do seu código de interoperação.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher e o loop de mensagem  
 Um cenário normal para interoperação e suporte a eventos de teclado é implementar <xref:System.Windows.Interop.IKeyboardInputSink>ou a subclasse de classes que já implementam <xref:System.Windows.Interop.IKeyboardInputSink>, como <xref:System.Windows.Interop.HwndSource> ou <xref:System.Windows.Interop.HwndHost>. No entanto, o suporte ao coletor de teclado não trata de todas as necessidades de loop de mensagem possíveis que você pode ter ao enviar e receber mensagens entre os limites de interoperação. Para ajudar a formalizar uma arquitetura de loop de mensagem de aplicativo, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece a classe <xref:System.Windows.Interop.ComponentDispatcher>, que define um protocolo simples para que um loop de mensagem seja seguido.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> é uma classe estática que expõe vários membros. O escopo de cada método é unido implicitamente ao thread de chamada. Um loop de mensagem deve chamar algumas dessas APIs em momentos críticos (conforme definido na próxima seção).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> fornece eventos que outros componentes (como o coletor de teclado) podem escutar. A classe <xref:System.Windows.Threading.Dispatcher> chama todos os métodos de <xref:System.Windows.Interop.ComponentDispatcher> apropriados em uma sequência apropriada. Se você estiver implementando seu próprio loop de mensagem, seu código será responsável por chamar <xref:System.Windows.Interop.ComponentDispatcher> métodos de maneira semelhante.  
  
 Chamar <xref:System.Windows.Interop.ComponentDispatcher> métodos em um thread só invocará manipuladores de eventos que foram registrados nesse thread.  
  
## <a name="writing-message-loops"></a>Escrevendo loops de mensagem  
 Veja a seguir uma lista de verificação de <xref:System.Windows.Interop.ComponentDispatcher> Membros que você usará se escrever seu próprio loop de mensagem:  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: seu loop de mensagem deve chamá-lo para indicar que o thread é modal.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: seu loop de mensagem deve chamá-lo para indicar que o thread foi revertido para não modal.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: seu loop de mensagem deve chamá-lo para indicar que <xref:System.Windows.Interop.ComponentDispatcher> deve gerar o evento <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>. <xref:System.Windows.Interop.ComponentDispatcher> não gerará <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> se <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> for `true`, mas os loops de mensagem poderão optar por chamar <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> mesmo se <xref:System.Windows.Interop.ComponentDispatcher> não puder responder a ela enquanto estiver no estado modal.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: seu loop de mensagem deve chamá-lo para indicar que uma nova mensagem está disponível. O valor de retorno indica se um ouvinte para um evento de <xref:System.Windows.Interop.ComponentDispatcher> tratou a mensagem. Se <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> retornar `true` (manipulado), o Dispatcher não deverá fazer nada mais com a mensagem. Se o valor de retorno for `false`, o Dispatcher deverá chamar a função do Win32 `TranslateMessage`e, em seguida, chamar `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>Usando ComponentDispatcher e manipulando mensagens existentes  
 A seguir está uma lista de verificação de <xref:System.Windows.Interop.ComponentDispatcher> Membros que você usará se você depender do loop de mensagem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inerente.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: retorna se o aplicativo tornou-se modal (por exemplo, um loop de mensagem modal foi enviado por push). <xref:System.Windows.Interop.ComponentDispatcher> pode rastrear esse estado porque a classe mantém uma contagem de chamadas de <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> e <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> do loop de mensagem.  
  
- eventos de <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> e <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> seguem as regras padrão para invocações de delegado. Representantes são invocados em ordem não especificada e todos os representantes são invocados, mesmo que o primeiro marca a mensagem como tratada.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: indica um tempo apropriado e eficiente para o processamento ocioso (não há outras mensagens pendentes para o thread). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> não será gerado se o thread for modal.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: gerado para todas as mensagens processadas pela bomba de mensagens.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: gerado para todas as mensagens que não foram manipuladas durante <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Uma mensagem é considerada tratada se, após o evento de <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> ou evento de <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>, o parâmetro `handled` passado por referência nos dados do evento for `true`. Manipuladores de evento devem ignorar a mensagem se `handled` for `true`, pois isso significa que o manipulador diferente a tratou primeiro. Manipuladores de eventos dos dois eventos podem modificar a mensagem. O despachante deve despachar a mensagem modificada e não a mensagem original inalterada. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> é entregue a todos os ouvintes, mas a intenção da arquitetura é que apenas a janela de nível superior que contém o HWND no qual as mensagens direcionadas deve invocar o código em resposta à mensagem.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>Como HwndSource trata eventos de ComponentDispatcher  
 Se a <xref:System.Windows.Interop.HwndSource> for uma janela de nível superior (sem HWND pai), ela será registrada com <xref:System.Windows.Interop.ComponentDispatcher>. Se <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> for gerado e se a mensagem for destinada para as janelas <xref:System.Windows.Interop.HwndSource> ou filho, <xref:System.Windows.Interop.HwndSource> chamará seu <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> sequência de coletor de teclado.  
  
 Se o <xref:System.Windows.Interop.HwndSource> não for uma janela de nível superior (tem um HWND pai), não haverá manipulação. Somente a janela de nível superior deve realizar o tratamento e espera-se que haja uma janela de nível superior com suporte para coletor de teclado como parte de qualquer cenário de interoperação.  
  
 Se <xref:System.Windows.Interop.HwndHost.WndProc%2A> em um <xref:System.Windows.Interop.HwndSource> for chamado sem um método de coletor de teclado apropriado sendo chamado primeiro, seu aplicativo receberá os eventos de teclado de nível superior, como <xref:System.Windows.UIElement.KeyDown>. No entanto, nenhum método de coletor de teclado será chamado, o que contorna recursos de modelo de entrada do teclado desejáveis, como suporte para chave de acesso. Isso pode acontecer porque o loop de mensagem não notificava corretamente o thread relevante no <xref:System.Windows.Interop.ComponentDispatcher>, ou porque o HWND pai não invocau as respostas adequadas do coletor de teclado.  
  
 Uma mensagem que vai para o coletor de teclado pode não ser enviada para o HWND se você adicionou ganchos para essa mensagem usando o método <xref:System.Windows.Interop.HwndSource.AddHook%2A>. A mensagem pode ser sido tratada no nível de bomba de mensagens diretamente e não enviada para a função `DispatchMessage`.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md)
- [Modelo de threading](threading-model.md)
- [Visão geral da entrada](input-overview.md)
