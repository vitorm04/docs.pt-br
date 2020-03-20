---
title: Hospede um controle Win32 no WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 5185e60640c652b79bd105db54830ac3acc57129
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186747"
---
# <a name="walkthrough-host-a-win32-control-in-wpf"></a>Passo a passo: hospede um controle Win32 no WPF
O Windows Presentation Foundation (WPF) fornece um ambiente rico para criar aplicativos. No entanto, quando você tem um investimento substancial no código Win32, pode ser mais eficaz reutilizar pelo menos parte desse código em seu aplicativo WPF em vez de reescrevê-lo completamente. O WPF fornece um mecanismo simples para hospedar uma janela Win32, em uma página do WPF.  
  
 Este tópico orienta você através de um aplicativo, [hospedando um Controle Win32 ListBox no WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), que hospeda um controle de caixa de lista Win32. Este procedimento geral pode ser estendido para hospedar qualquer janela Win32.  

<a name="requirements"></a>
## <a name="requirements"></a>Requisitos  
 Este tópico assume uma familiaridade básica com a programação da API WPF e windows. Para uma introdução básica à programação do WPF, consulte [Getting Started](../getting-started/index.md). Para uma introdução à programação da API do Windows, consulte qualquer um dos inúmeros livros sobre o assunto, em particular *O Windows de Programação* por Charles Petzold.  
  
 Como a amostra que acompanha esse tópico é implementada em C#, ela faz uso do Platform Invocation Services (PInvoke) para acessar a API do Windows. Alguma familiaridade com o PInvoke é útil, mas não essencial.  
  
> [!NOTE]
> Este tópico inclui alguns exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Você pode obter ou exibir código completo a partir da [hospedagem de um controle Win32 ListBox na amostra WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>O procedimento básico  
 Esta seção descreve o procedimento básico para hospedar uma janela Win32 em uma página do WPF. As seções restantes apresentam detalhes de cada etapa.  
  
 O procedimento básico de hospedagem é:  
  
1. Implemente uma página Do WPF para hospedar a janela. Uma técnica é <xref:System.Windows.Controls.Border> criar um elemento para reservar uma seção da página para a janela hospedada.  
  
2. Implementar uma classe para hospedar o <xref:System.Windows.Interop.HwndHost>controle que herda de .  
  
3. Nessa classe, anule <xref:System.Windows.Interop.HwndHost> o <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>membro da classe.  
  
4. Crie a janela hospedada como uma criança da janela que contém a página WPF. Embora a programação convencional do WPF não precise fazer uso explícito dela, a página de hospedagem é uma janela com uma alça (HWND). Você recebe a página HWND através do `hwndParent` parâmetro do <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> método. A janela hospedada deve ser criada como um filho desse HWND.  
  
5. Depois de criar a janela do host, retorne o HWND da janela hospedada. Se você quiser hospedar um ou mais controles Win32, você normalmente cria uma janela de hospedagem como uma criança do HWND e faz os controles crianças dessa janela de host. Envolver os controles em uma janela de host fornece uma maneira simples para que sua página do WPF receba notificações dos controles, que lida com alguns problemas específicos do Win32 com notificações através do limite HWND.  
  
6. Manipule as mensagens selecionadas enviadas à janela de host, como notificações dos controles filho. Há duas maneiras de fazer isso.  
  
    - Se você preferir manusear mensagens em <xref:System.Windows.Interop.HwndHost.WndProc%2A> sua classe <xref:System.Windows.Interop.HwndHost> de hospedagem, anule o método da classe.  
  
    - Se você preferir que o WPF manuseie as mensagens, manuseie o <xref:System.Windows.Interop.HwndHost> evento de classe <xref:System.Windows.Interop.HwndHost.MessageHook> em seu código-trás. Esse evento ocorre para cada mensagem recebida pela janela hospedada. Se você escolher essa opção, <xref:System.Windows.Interop.HwndHost.WndProc%2A>você ainda deve substituir, mas você só precisa de uma implementação mínima.  
  
7. Anular os <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> <xref:System.Windows.Interop.HwndHost.WndProc%2A> métodos <xref:System.Windows.Interop.HwndHost>de . Você deve substituir esses métodos <xref:System.Windows.Interop.HwndHost> para satisfazer o contrato, mas você pode apenas precisar fornecer uma implementação mínima.  
  
8. Em seu arquivo de código atrás, crie uma instância da classe <xref:System.Windows.Controls.Border> de hospedagem de controle e torne-a uma criança do elemento que se destina a hospedar a janela.  
  
9. Comunique-se com a janela hospedada enviando-lhe mensagens do Microsoft Windows e manipulando mensagens de suas janelas de crianças, como notificações enviadas por controles.  
  
<a name="page_layout"></a>
## <a name="implement-the-page-layout"></a>Implementar o layout da página  
 O layout para a página WPF que hospeda o Controle ListBox consiste em duas regiões. O lado esquerdo da página hospeda vários [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] controles WPF que fornecem um que permite manipular o controle Win32. O canto superior direito da página tem uma região quadrada para o controle ListBox hospedado.  
  
 O código para implementar este layout é bastante simples. O elemento raiz <xref:System.Windows.Controls.DockPanel> é um que tem dois elementos infantis. O primeiro <xref:System.Windows.Controls.Border> é um elemento que hospeda o Controle ListBox. Ele ocupa um quadrado de 200x200 no canto superior direito da página. O segundo <xref:System.Windows.Controls.StackPanel> é um elemento que contém um conjunto de controles WPF que exibem informações e permitem manipular o Controle ListBox definindo propriedades de interoperação expostas. Para cada um dos elementos <xref:System.Windows.Controls.StackPanel>que são filhos do , veja o material de referência para os vários elementos utilizados para detalhes sobre o que esses elementos são ou o que eles fazem, estes estão listados no código de exemplo abaixo, mas não serão explicados aqui (o modelo básico de interoperação não requer nenhum deles, eles são fornecidos para adicionar alguma interatividade à amostra).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementar uma classe para hospedar o controle Microsoft Win32  
 O núcleo dessa amostra é a classe que realmente hospeda o controle: ControlHost.cs. Herda de <xref:System.Windows.Interop.HwndHost>. O construtor tem dois parâmetros, altura e largura, que <xref:System.Windows.Controls.Border> correspondem à altura e largura do elemento que hospeda o controle ListBox. Esses valores são usados posteriormente para <xref:System.Windows.Controls.Border> garantir que o tamanho do controle corresponda ao elemento.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Também existe um conjunto de constantes. Essas constantes são em grande parte tiradas do Winuser.h, e permitem que você use nomes convencionais ao chamar funções Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Substituir o BuildWindowCore para criar a janela do Microsoft Win32  
 Você anula este método para criar a janela Win32 que será hospedada pela página e faz a conexão entre a janela e a página. Como essa amostra envolve a hospedagem de um controle ListBox, duas janelas são criadas. A primeira é a janela que é realmente hospedada pela página WPF. O controle ListBox é criado como um filho dessa janela.  
  
 A razão para essa abordagem é simplificar o processo de recebimento de notificações do controle. A <xref:System.Windows.Interop.HwndHost> classe permite processar mensagens enviadas para a janela que está hospedando. Se você hospedar diretamente um controle Win32, você receberá as mensagens enviadas para o loop de mensagem interna do controle. É possível exibir o controle e lhe enviar mensagens, mas você não receberá as notificações que o controle envia para a janela pai. Isso significa, entre outras coisas, que você não tem nenhuma maneira de detectar quando o usuário interage com o controle. Em vez disso, crie uma janela de host e transforme o controle em filho dessa janela. Assim, pode processar as mensagens para a janela de host, incluindo as notificações enviadas a ela pelo controle. Por uma questão de conveniência, como a janela de host é mais que um wrapper simples para o controle, o pacote será chamado de controle ListBox.  
  
<a name="create_the_window_and_listbox"></a>
#### <a name="create-the-host-window-and-listbox-control"></a>Criar a janela de host e o controle ListBox  
 Você pode usar o PInvoke para criar uma janela de host para o controle criando e registrando uma classe de janela, e assim por diante. No entanto, uma abordagem muito mais simples é criar uma janela com a classe de janela predefinida “estática”. Isso proporciona o procedimento de janela de que você precisa para receber notificações do controle e requer o mínimo de codificação.  
  
 O HWND do controle é exposto por meio de uma propriedade somente leitura; assim, a página de host pode usá-lo para enviar mensagens para o controle.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 O controle ListBox é criado como um filho da janela de host. A altura e a largura de ambas as janelas são definidas para os valores passados para o construtor, discutidos acima. Isso garante que o tamanho da janela de host e do controle sejam idênticos à área reservada na página.  Depois que as janelas são criadas, a amostra retorna um <xref:System.Runtime.InteropServices.HandleRef> objeto que contém o HWND da janela do host.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>
### <a name="implement-destroywindow-and-wndproc"></a>Implementar DestroyWindow e WndProc  
 Além <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>disso, você também deve <xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> substituir os <xref:System.Windows.Interop.HwndHost>métodos e métodos do . Neste exemplo, as mensagens para o controle <xref:System.Windows.Interop.HwndHost.MessageHook> são tratadas <xref:System.Windows.Interop.HwndHost.WndProc%2A> pelo <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> manipulador, assim a implementação e é mínima. No caso <xref:System.Windows.Interop.HwndHost.WndProc%2A>de `handled` , `false` definido para indicar que a mensagem não foi tratada e retornar 0. Pois, <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>basta destruir a janela.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>
## <a name="host-the-control-on-the-page"></a>Hospedar o controle na página  
 Para hospedar o controle na página, primeiro crie `ControlHost` uma nova instância da classe. Passe a altura e a largura do`ControlHostElement`elemento de `ControlHost` borda que contém o controle ( ) para o construtor. Isso garante que o ListBox será dimensionado corretamente. Em seguida, você hospeda o `ControlHost` controle na <xref:System.Windows.Controls.Decorator.Child%2A> página atribuindo o objeto à propriedade do host <xref:System.Windows.Controls.Border>.  
  
 A amostra anexa um <xref:System.Windows.Interop.HwndHost.MessageHook> manipulador ao `ControlHost` evento de receber mensagens do controle. Esse evento é gerado para cada mensagem enviada para a janela hospedada. Nesse caso, são as mensagens enviadas à janela que encapsula o verdadeiro controle ListBox, incluindo notificações do controle. O exemplo chama SendMessage para obter informações do controle e modificar seu conteúdo. Os detalhes de como a página se comunica com o controle são discutidos na próxima seção.  
  
> [!NOTE]
> Observe que existem duas declarações PInvoke para SendMessage. Isso é necessário porque `wParam` um usa o parâmetro para passar uma string e o outro usa-o para passar um inteiro. Você precisa de uma declaração separada para cada assinatura a fim de garantir que o marshaling dos dados será realizado corretamente.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementar comunicação entre o controle e a página  
 Você manipula o controle enviando-lhe mensagens do Windows. Para notificar você de que o usuário interagiu com ele, o controle envia notificações para a janela de host. O [Controle Hosting a Win32 ListBox na](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) amostra WPF inclui uma ui que fornece vários exemplos de como isso funciona:  
  
- Acrescentar um novo item à lista.  
  
- Excluir o item selecionado da lista  
  
- Exibir o texto do item selecionado atualmente.  
  
- Exibir o número de itens na lista.  
  
 O usuário também pode selecionar um item na caixa de lista clicando nele, assim como faria com um aplicativo Win32 convencional. Os dados exibidos são atualizados sempre que o usuário altera o estado da caixa de listagem ao selecionar, adicionar ou acrescentar um item.  
  
 Para anexar itens, envie uma [ `LB_ADDSTRING` mensagem](/windows/desktop/Controls/lb-addstring)à caixa de lista . Para excluir itens, [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) envie para obter o índice [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) da seleção atual e, em seguida, para excluir o item. A amostra [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)também envia , e usa o valor retornado para atualizar o display que mostra o número de itens. Ambas as [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) instâncias de uso de uma das declarações pinvoke discutidas na seção anterior.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Quando o usuário seleciona um item ou altera sua seleção, o controle notifica a janela do host enviando-lhe uma <xref:System.Windows.Interop.HwndHost.MessageHook> [ `WM_COMMAND` mensagem](/windows/desktop/menurc/wm-command), o que eleva o evento para a página. O manipulador recebe as mesmas informações que o procedimento de janela principal da janela de host. Ele também passa uma referência a `handled`um valor booleano, . Você `handled` decidiu `true` indicar que lidou com a mensagem e nenhum processamento adicional é necessário.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)é enviado por uma variedade de razões, então você deve examinar o ID de notificação para determinar se é um evento que você deseja lidar. O ID está contido na `wParam` palavra alta do parâmetro. A amostra usa operadores bitwise para extrair o ID. Se o usuário tiver feito ou alterado sua [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)seleção, o ID será .  
  
 Quando [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) é recebida, a amostra obtém o índice do item selecionado enviando ao controle uma [ `LB_GETCURSEL` mensagem](/windows/desktop/Controls/lb-getcursel). Para obter o texto, <xref:System.Text.StringBuilder>primeiro você cria um . Em seguida, envie uma [ `LB_GETTEXT` mensagem](/windows/desktop/Controls/lb-gettext)ao controle. Passe o <xref:System.Text.StringBuilder> objeto `wParam` vazio como parâmetro. Quando [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) retornar, <xref:System.Text.StringBuilder> o texto do item selecionado. Este uso [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) requer mais uma declaração PInvoke.  
  
 Finalmente, `handled` definido `true` para indicar que a mensagem foi tratada.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Interop.HwndHost>
- [Interoperação do WPF e do Win32](wpf-and-win32-interoperation.md)
- [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
