---
title: Arquitetura de entrada de interoperabilidade do Windows Forms e do WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- input architecture [WPF interoperability]
- messages [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- modeless forms [WPF]
- ElementHost keyboard and messages [WPF]
- keyboard interoperation [WPF]
- WindowsFormsHost keyboard and messages [WPF]
- modeless dialog boxes [WPF]
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
ms.openlocfilehash: f79971ba13691ccc36420e39696b7b8a46e5ce0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745054"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows Forms e arquitetura de entrada da interoperabilidade do WPF
A interoperação entre o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] requer que as duas tecnologias tenham o processamento de entrada de teclado apropriado. Este tópico descreve como essas tecnologias implementam o processamento de mensagens e teclado para permitir uma interoperação suave em aplicativos híbridos.  
  
 Este tópico contém as seguintes subseções:  
  
- Formulários sem janela restrita e caixas de diálogo  
  
- Processamento de mensagens e teclado de WindowsFormsHost  
  
- Processamento de mensagens e teclado de ElementHost  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Formulários sem janela restrita e caixas de diálogo  
 Chame o método <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> no elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> para abrir um formulário ou caixa de diálogo sem janela restrita de um aplicativo baseado em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Chame o método <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> no controle de <xref:System.Windows.Forms.Integration.ElementHost> para abrir uma página de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sem janela restrita em um aplicativo baseado em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>Processamento de mensagens e teclado de WindowsFormsHost  
 Quando hospedado por um aplicativo baseado em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o processamento de mensagens e teclado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] consiste no seguinte:  
  
- A classe <xref:System.Windows.Forms.Integration.WindowsFormsHost> adquire mensagens do loop de mensagem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], que é implementado pela classe <xref:System.Windows.Interop.ComponentDispatcher>.  
  
- A classe <xref:System.Windows.Forms.Integration.WindowsFormsHost> cria um loop de mensagem de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] substituto para garantir que o processamento de teclado de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] comum ocorra.  
  
- A classe <xref:System.Windows.Forms.Integration.WindowsFormsHost> implementa a interface <xref:System.Windows.Interop.IKeyboardInputSink> para coordenar o gerenciamento de foco com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Os controles de <xref:System.Windows.Forms.Integration.WindowsFormsHost> se registram e iniciam seus loops de mensagens.  
  
 As seções a seguir descrevem essas etapas do processo em mais detalhes.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Adquirindo mensagens do loop de mensagens do WPF  
 A classe <xref:System.Windows.Interop.ComponentDispatcher> implementa o Gerenciador de loop de mensagem para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A classe <xref:System.Windows.Interop.ComponentDispatcher> fornece ganchos para permitir que clientes externos filtrem mensagens antes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processá-las.  
  
 A implementação de interoperação manipula o evento <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>, que permite que [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles processem mensagens antes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Loop de mensagens substituto dos Windows Forms  
 Por padrão, a classe <xref:System.Windows.Forms.Application?displayProperty=nameWithType> contém o loop de mensagem principal para [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplicativos. Durante a interoperação, o loop de mensagens [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não processa mensagens. Portanto, essa lógica deve ser reproduzida. O manipulador para o evento <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> executa as seguintes etapas:  
  
1. Filtra a mensagem usando a interface <xref:System.Windows.Forms.IMessageFilter>.  
  
2. Chama o método <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>.  
  
3. Converte e envia a mensagem, se necessário.  
  
4. Passa a mensagem para o controle de host, se nenhum outro controle processar a mensagem.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implementação de IKeyboardInputSink  
 O loop de mensagens substituto trata do gerenciamento do teclado. Portanto, o método <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> é o único membro <xref:System.Windows.Interop.IKeyboardInputSink> que requer uma implementação na classe <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Por padrão, a classe <xref:System.Windows.Interop.HwndHost> retorna `false` para sua implementação de <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>. Isso evita a tabulação de um controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para um controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 A implementação de <xref:System.Windows.Forms.Integration.WindowsFormsHost> do método <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> executa as seguintes etapas:  
  
1. Localiza o primeiro ou último controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] que está contido pelo controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> e que pode receber o foco. A escolha do controle depende de informações de passagem.  
  
2. Define o foco para o controle e retorna `true`.  
  
3. Se nenhum controle puder receber o foco, retorna `false`.  
  
### <a name="windowsformshost-registration"></a>Registro de WindowsFormsHost  
 Quando o identificador de janela para um controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> é criado, o controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> chama um método estático interno que registra sua presença para o loop de mensagem.  
  
 Durante o registro, o controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> examina o loop de mensagem. Se o loop de mensagem não tiver sido iniciado, o manipulador de eventos <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> será criado. O loop de mensagem é considerado em execução quando o manipulador de eventos <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> é anexado.  
  
 Quando o identificador de janela é destruído, o controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> se remove do registro.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>Processamento de mensagens e teclado de ElementHost  
 Quando hospedado por um aplicativo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], o processamento de mensagens e teclado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste no seguinte:  
  
- implementações de interface <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>e <xref:System.Windows.Interop.IKeyboardInputSite>.  
  
- Teclas de direção e tabulação.  
  
- Teclas de comando e teclas de caixa de diálogo.  
  
- Processamento do acelerador [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 As seções a seguir descrevem essas partes em mais detalhes.  
  
### <a name="interface-implementations"></a>Implementações de interfaces  
 Em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], as mensagens de teclado são encaminhadas para o identificador de janela do controle que tem o foco. No controle de <xref:System.Windows.Forms.Integration.ElementHost>, essas mensagens são roteadas para o elemento hospedado. Para fazer isso, o controle de <xref:System.Windows.Forms.Integration.ElementHost> fornece uma instância de <xref:System.Windows.Interop.HwndSource>. Se o controle de <xref:System.Windows.Forms.Integration.ElementHost> tiver foco, a instância de <xref:System.Windows.Interop.HwndSource> roteará a maioria das entradas de teclado para que possa ser processada pela classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager>.  
  
 A classe <xref:System.Windows.Interop.HwndSource> implementa as interfaces <xref:System.Windows.Interop.IKeyboardInputSink> e <xref:System.Windows.Interop.IKeyboardInputSite>.  
  
 A interoperação de teclado depende da implementação do método <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> para manipular a tecla TAB e a entrada da tecla de seta que move o foco dos elementos hospedados.  
  
### <a name="tabbing-and-arrow-keys"></a>Teclas de direção e tabulação  
 A lógica de seleção de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é mapeada para os métodos <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> e <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> para implementar a navegação de tecla TAB e Arrow. A substituição do método <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> realiza esse mapeamento.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Teclas de comando e teclas de caixa de diálogo  
 Para dar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] primeira oportunidade de processar chaves de comando e chaves de diálogo, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pré-processamento de comando é conectado ao método <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>. Substituir o método <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> conecta as duas tecnologias.  
  
 Com o método <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>, os elementos hospedados podem manipular qualquer mensagem de chave, como WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN ou WM_SYSKEYUP, incluindo as teclas de comando, como TAB, ENTER, ESC e teclas de direção. Se uma mensagem de tecla não for tratada, ela será enviada para a hierarquia ancestral de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] para que seja tratada.  
  
### <a name="accelerator-processing"></a>Processamento do acelerador  
 Para processar aceleradores corretamente, o processamento do acelerador de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] deve estar conectado à classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager>. Além disso, todas as mensagens WM_CHAR devem ser encaminhadas corretamente para os elementos hospedados.  
  
 Como a implementação padrão de <xref:System.Windows.Interop.HwndSource> do método <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> retorna `false`, WM_CHAR mensagens são processadas usando a seguinte lógica:  
  
- O método <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> é substituído para garantir que todas as mensagens de WM_CHAR sejam encaminhadas para elementos hospedados.  
  
- Se a tecla ALT estiver pressionada, a mensagem será WM_SYSCHAR. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não processa essa mensagem por meio do método <xref:System.Windows.Forms.Control.IsInputChar%2A>. Portanto, o método <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> é substituído para consultar o <xref:System.Windows.Input.AccessKeyManager> de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para um acelerador registrado. Se um acelerador registrado for encontrado, <xref:System.Windows.Input.AccessKeyManager> o processará.  
  
- Se a tecla ALT não for pressionada, a classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> processará a entrada sem tratamento. Se a entrada for um acelerador, o <xref:System.Windows.Input.AccessKeyManager> o processará. O evento <xref:System.Windows.Input.InputManager.PostProcessInput> é tratado para WM_CHAR mensagens que não foram processadas.  
  
 Quando o usuário pressiona a tecla ALT, indicações visuais do acelerador são mostradas em todo o formulário. Para dar suporte a esse comportamento, todos os controles de <xref:System.Windows.Forms.Integration.ElementHost> no formulário ativo recebem WM_SYSKEYDOWN mensagens, independentemente de qual controle tenha foco.  
  
 As mensagens são enviadas somente para <xref:System.Windows.Forms.Integration.ElementHost> controles no formulário ativo.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Passo a passo: hospedando um controle composto do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: hospedando um controle composto do WPF no Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md)
