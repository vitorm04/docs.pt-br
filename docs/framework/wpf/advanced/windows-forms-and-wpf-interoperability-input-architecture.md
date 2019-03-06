---
title: Windows Forms e arquitetura de entrada da interoperabilidade do WPF
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
ms.openlocfilehash: 50097ef86fb6bc5341d7ea16ccee441b89823401
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352409"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows Forms e arquitetura de entrada da interoperabilidade do WPF
A interoperação entre o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] requer que as duas tecnologias tenham o processamento de entrada de teclado apropriado. Este tópico descreve como essas tecnologias implementam o processamento de mensagens e teclado para permitir uma interoperação suave em aplicativos híbridos.  
  
 Este tópico contém as seguintes subseções:  
  
-   Formulários sem janela restrita e caixas de diálogo  
  
-   Processamento de mensagens e teclado de WindowsFormsHost  
  
-   Processamento de mensagens e teclado de ElementHost  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Formulários sem janela restrita e caixas de diálogo  
 Chamar o <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> método na <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento para abrir uma caixa de diálogo ou formulário sem janela restrita de um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-com base em aplicativo.  
  
 Chame o <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> método na <xref:System.Windows.Forms.Integration.ElementHost> controle para abrir uma sem janela restrita [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página em um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-aplicativo baseado em.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>Processamento de mensagens e teclado de WindowsFormsHost  
 Quando hospedado por um aplicativo baseado em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o processamento de mensagens e teclado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] consiste no seguinte:  
  
-   O <xref:System.Windows.Forms.Integration.WindowsFormsHost> classe adquire mensagens do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] loop de mensagem, que é implementado pelo <xref:System.Windows.Interop.ComponentDispatcher> classe.  
  
-   O <xref:System.Windows.Forms.Integration.WindowsFormsHost> classe cria um substituto [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] loop de mensagem para garantir que os normais [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ocorre o processamento de teclado.  
  
-   O <xref:System.Windows.Forms.Integration.WindowsFormsHost> classe implementa as <xref:System.Windows.Interop.IKeyboardInputSink> interface para coordenar o gerenciamento de foco com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   O <xref:System.Windows.Forms.Integration.WindowsFormsHost> controles se registram e iniciam seus loops de mensagens.  
  
 As seções a seguir descrevem essas etapas do processo em mais detalhes.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Adquirindo mensagens do loop de mensagens do WPF  
 O <xref:System.Windows.Interop.ComponentDispatcher> classe implementa o Gerenciador de loop de mensagem para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O <xref:System.Windows.Interop.ComponentDispatcher> classe fornece ganchos para permitir que clientes externos filtrem mensagens antes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processa.  
  
 A implementação de interoperação trata os <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> evento, que permite [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles processem mensagens antes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Loop de mensagens substituto dos Windows Forms  
 Por padrão, o <xref:System.Windows.Forms.Application?displayProperty=nameWithType> classe contém o loop de mensagem principal para [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplicativos. Durante a interoperação, o loop de mensagens [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não processa mensagens. Portanto, essa lógica deve ser reproduzida. O manipulador para o <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> eventos executa as seguintes etapas:  
  
1.  Filtra a mensagem usando o <xref:System.Windows.Forms.IMessageFilter> interface.  
  
2.  Chama o método <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>.  
  
3.  Converte e envia a mensagem, se necessário.  
  
4.  Passa a mensagem para o controle de host, se nenhum outro controle processar a mensagem.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implementação de IKeyboardInputSink  
 O loop de mensagens substituto trata do gerenciamento do teclado. Portanto, o <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> método é a única <xref:System.Windows.Interop.IKeyboardInputSink> membro que requer uma implementação no <xref:System.Windows.Forms.Integration.WindowsFormsHost> classe.  
  
 Por padrão, o <xref:System.Windows.Interop.HwndHost> classe retorna `false` para seu <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> implementação. Isso evita a tabulação de um controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para um controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 O <xref:System.Windows.Forms.Integration.WindowsFormsHost> implementação do <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> método executa as seguintes etapas:  
  
1.  Localiza o primeiro ou último [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle que está contido pelo <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle e que pode receber o foco. A escolha do controle depende de informações de passagem.  
  
2.  Define o foco para o controle e retorna `true`.  
  
3.  Se nenhum controle puder receber o foco, retorna `false`.  
  
### <a name="windowsformshost-registration"></a>Registro de WindowsFormsHost  
 Quando a janela de identificador para um <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle é criado, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle chama um método estático interno que registra sua presença no loop de mensagens.  
  
 Durante o registro, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle examina o loop de mensagem. Se o loop de mensagem não foi iniciado, o <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> manipulador de eventos é criado. O loop de mensagem é considerado para estar em execução quando o <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> manipulador de eventos está anexado.  
  
 Quando o identificador de janela é destruído, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle remove a próprio no registro.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>Processamento de mensagens e teclado de ElementHost  
 Quando hospedado por um aplicativo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], o processamento de mensagens e teclado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste no seguinte:  
  
-   <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>, e <xref:System.Windows.Interop.IKeyboardInputSite> implementações de interface.  
  
-   Teclas de direção e tabulação.  
  
-   Teclas de comando e teclas de caixa de diálogo.  
  
-   Processamento do acelerador [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 As seções a seguir descrevem essas partes em mais detalhes.  
  
### <a name="interface-implementations"></a>Implementações de interfaces  
 Em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], as mensagens de teclado são encaminhadas para o identificador de janela do controle que tem o foco. No <xref:System.Windows.Forms.Integration.ElementHost> controle, essas mensagens são roteadas para o elemento hospedado. Para fazer isso, o <xref:System.Windows.Forms.Integration.ElementHost> controle fornece uma <xref:System.Windows.Interop.HwndSource> instância. Se o <xref:System.Windows.Forms.Integration.ElementHost> controle tem o foco, o <xref:System.Windows.Interop.HwndSource> instância encaminha a maioria dos teclado de entrada para que ela possa ser processada pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> classe.  
  
 O <xref:System.Windows.Interop.HwndSource> classe implementa as <xref:System.Windows.Interop.IKeyboardInputSink> e <xref:System.Windows.Interop.IKeyboardInputSite> interfaces.  
  
 Interoperação de teclado depende da implementação o <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> método de identificador de chave de guia e seta para a entrada que move o foco para fora de elementos hospedados da chave.  
  
### <a name="tabbing-and-arrow-keys"></a>Teclas de direção e tabulação  
 O [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lógica de seleção é mapeada para o <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> e <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> navegação de chave de métodos para implementar a direção e TAB. Substituindo o <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> método realiza esse mapeamento.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Teclas de comando e teclas de caixa de diálogo  
 Para dar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a primeira oportunidade de processar teclas de comando e teclas de caixa de diálogo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pré-processamento de comando está conectado ao <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> método. Substituindo o <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> método conecta as duas tecnologias.  
  
 Com o <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> método, os elementos hospedados podem tratar qualquer mensagem de tecla, como WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN ou WM_SYSKEYUP, incluindo teclas de comando, como teclas de seta, ENTER, ESC e TAB. Se uma mensagem de tecla não for tratada, ela será enviada para a hierarquia ancestral de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] para que seja tratada.  
  
### <a name="accelerator-processing"></a>Processamento do acelerador  
 Para processar aceleradores corretamente, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] processamento do acelerador deve estar conectado para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> classe. Além disso, todas as mensagens WM_CHAR devem ser encaminhadas corretamente para os elementos hospedados.  
  
 Porque o padrão <xref:System.Windows.Interop.HwndSource> implementação do <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> retorno do método `false`, as mensagens WM_CHAR são processadas usando a seguinte lógica:  
  
-   O <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> método é substituído para garantir que todas as mensagens WM_CHAR são encaminhadas para elementos hospedados.  
  
-   Se a tecla ALT estiver pressionada, a mensagem será WM_SYSCHAR. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não pré-processa esta mensagem por meio de <xref:System.Windows.Forms.Control.IsInputChar%2A> método. Portanto, o <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> método é substituído para consultar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> para um acelerador registrado. Se um acelerador registrado for encontrado, <xref:System.Windows.Input.AccessKeyManager> processa-os.  
  
-   Se a tecla ALT não estiver pressionada, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> classe processa a entrada não tratada. Se a entrada é um acelerador, o <xref:System.Windows.Input.AccessKeyManager> processa-os. O <xref:System.Windows.Input.InputManager.PostProcessInput> evento é tratado para mensagens WM_CHAR que não foram processadas.  
  
 Quando o usuário pressiona a tecla ALT, indicações visuais do acelerador são mostradas em todo o formulário. Para dar suporte a esse comportamento, todos os <xref:System.Windows.Forms.Integration.ElementHost> controles no formulário ativo recebem mensagens WM_SYSKEYDOWN, independentemente de qual controle tem o foco.  
  
 As mensagens são enviadas somente ao <xref:System.Windows.Forms.Integration.ElementHost> controles no formulário ativo.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Passo a passo: Hospedando um controle composto do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto do WPF nos Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Interoperação do WPF e do Win32](wpf-and-win32-interoperation.md)
