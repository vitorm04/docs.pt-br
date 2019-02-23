---
title: 'Passo a passo: Hospedando um controle Win32 no WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 047ccd4ea4ba83c8d7427559f3ee76cc3547a430
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747525"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Passo a passo: Hospedando um controle Win32 no WPF
Windows Presentation Foundation (WPF) fornece um ambiente rico para a criação de aplicativos. No entanto, quando você tem um investimento substancial em código Win32, pode ser mais eficiente reutilizar pelo menos parte desse código em seu aplicativo WPF em vez de reescrevê-lo completamente. O WPF fornece um mecanismo simples para hospedar uma janela do Win32, em uma página do WPF.  
  
 Este tópico orienta você por meio de um aplicativo [hospedando um controle Win32 ListBox no WPF de exemplo](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), que hosts de controle de uma caixa de listagem do Win32. Esse procedimento geral pode ser estendido para hospedar qualquer janela Win32.  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Este tópico pressupõe uma familiaridade básica com programação WPF e Win32. Para obter uma introdução básica à programação WPF, consulte [Introdução ao](../../../../docs/framework/wpf/getting-started/index.md). Para obter uma introdução à programação do Win32, você deve fazer referência a qualquer um dos vários livros sobre o assunto, em particular *Programming Windows* por Charles Petzold.  
  
 Como a amostra que acompanha este tópico é implementada no C#, ele faz uso dos serviços de invocação de plataforma (PInvoke) para acessar a API do Win32. Alguma familiaridade com PInvoke é útil, mas não são essenciais.  
  
> [!NOTE]
>  Este tópico inclui alguns exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Você pode obter ou exibir o código completo do [hospedando um controle Win32 ListBox no WPF de exemplo](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>O procedimento básico  
 Esta seção descreve o procedimento básico para hospedar uma janela do Win32 em uma página do WPF. As seções restantes apresentam detalhes de cada etapa.  
  
 O procedimento básico de hospedagem é:  
  
1.  Implemente uma página do WPF para hospedar a janela. Uma técnica é criar um <xref:System.Windows.Controls.Border> elemento para reservar uma seção da página para a janela hospedada.  
  
2.  Implemente uma classe para hospedar o controle que herda de <xref:System.Windows.Interop.HwndHost>.  
  
3.  Essa classe, substitua os <xref:System.Windows.Interop.HwndHost> membro da classe <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4.  Crie a janela hospedada como um filho da janela que contém a página do WPF. Embora a programação convencional do WPF não precisa fazer explicitamente usá-lo, a página de hospedagem é uma janela com um identificador (HWND). Você recebe o HWND da página por meio de `hwndParent` parâmetro do <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> método. A janela hospedada deve ser criada como um filho desse HWND.  
  
5.  Depois de criar a janela do host, retorne o HWND da janela hospedada. Se você quiser hospedar um ou mais controles do Win32, você normalmente cria uma janela de host como um filho do HWND e tornar os filhos de controles de janela de host. Encapsular os controles em uma janela host fornece uma maneira simples para sua página WPF receber notificações dos controles, que lida com alguns problemas específicos do Win32 com notificações além do limite HWND.  
  
6.  Manipule as mensagens selecionadas enviadas à janela de host, como notificações dos controles filho. Há duas formas de fazer isso.  
  
    -   Se você preferir manipular as mensagens na classe de hospedagem, substitua os <xref:System.Windows.Interop.HwndHost.WndProc%2A> método da <xref:System.Windows.Interop.HwndHost> classe.  
  
    -   Se você preferir que o WPF manipular as mensagens, lidar com o <xref:System.Windows.Interop.HwndHost> classe <xref:System.Windows.Interop.HwndHost.MessageHook> eventos em seu code-behind. Esse evento ocorre para cada mensagem recebida pela janela hospedada. Se você escolher essa opção, você ainda precisará substituir <xref:System.Windows.Interop.HwndHost.WndProc%2A>, mas você só precisa de uma implementação mínima.  
  
7.  Substituir a <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> e <xref:System.Windows.Interop.HwndHost.WndProc%2A> métodos de <xref:System.Windows.Interop.HwndHost>. Você deve substituir esses métodos para satisfazer o <xref:System.Windows.Interop.HwndHost> contrato, mas você só precisará fornecer uma implementação mínima.  
  
8.  No seu arquivo code-behind, crie uma instância da classe que hospeda controles e torná-lo um filho de <xref:System.Windows.Controls.Border> elemento se destina a hospedar a janela.  
  
9. Se comunicar com a janela hospedada, enviando- [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] mensagens e manipule mensagens das janelas filho, como notificações enviadas pelos controles.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementar o layout da página  
 O layout da página do WPF que hospeda o controle ListBox consiste em duas regiões. O lado esquerdo da página hospeda vários controles do WPF que fornecem um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] que permite que você manipule o controle do Win32. O canto superior direito da página tem uma região quadrada para o controle ListBox hospedado.  
  
 O código para implementar esse layout é bastante simple. O elemento raiz é um <xref:System.Windows.Controls.DockPanel> que tem dois elementos filho. A primeira é uma <xref:System.Windows.Controls.Border> elemento que hospeda o controle ListBox. Ele ocupa um quadrado de 200x200 no canto superior direito da página. O segundo é um <xref:System.Windows.Controls.StackPanel> expostos de elemento que contém um conjunto de controles do WPF que exibem informações e permitem que você manipule o controle ListBox, definindo propriedades de interoperação. Para cada um dos elementos que são filhos do <xref:System.Windows.Controls.StackPanel>, consulte o material de referência para os vários elementos usados para obter detalhes sobre esses elementos são ou o que eles fazem, eles estão listados no código de exemplo abaixo, mas não serão explicados aqui (o básico modelo de interoperação não exige qualquer um deles, eles são fornecidos para adicionar alguma interatividade ao exemplo).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementar uma classe para hospedar o controle Microsoft Win32  
 O núcleo dessa amostra é a classe que realmente hospeda o controle: ControlHost.cs. Herda de <xref:System.Windows.Interop.HwndHost>. O construtor aceita dois parâmetros, altura e largura, que correspondem à altura e largura do <xref:System.Windows.Controls.Border> elemento que hospeda o controle ListBox. Esses valores são usados mais tarde para garantir que o tamanho do controle corresponda a <xref:System.Windows.Controls.Border> elemento.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Também existe um conjunto de constantes. Essas constantes são basicamente extraídas do WinUser. h e permitem que você use nomes convencionais ao chamar funções do Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Substituir o BuildWindowCore para criar a janela do Microsoft Win32  
 Você substitui esse método para criar a janela do Win32 que será hospedada pela página e fazer a conexão entre a janela e a página. Como essa amostra envolve a hospedagem de um controle ListBox, duas janelas são criadas. A primeira é a janela que é realmente hospedada pela página do WPF. O controle ListBox é criado como um filho dessa janela.  
  
 A razão para essa abordagem é simplificar o processo de recebimento de notificações do controle. O <xref:System.Windows.Interop.HwndHost> classe permite que você processe as mensagens enviadas à janela que está hospedando. Se o host Win32 controlar diretamente, você receberá as mensagens enviadas para o loop de mensagem interno do controle. É possível exibir o controle e lhe enviar mensagens, mas você não receberá as notificações que o controle envia para a janela pai. Isso significa, entre outras coisas, que você não tem nenhuma maneira de detectar quando o usuário interage com o controle. Em vez disso, crie uma janela de host e transforme o controle em filho dessa janela. Assim, pode processar as mensagens para a janela de host, incluindo as notificações enviadas a ela pelo controle. Por uma questão de conveniência, como a janela de host é mais que um wrapper simples para o controle, o pacote será chamado de controle ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Criar a janela de host e o controle ListBox  
 Você pode usar PInvoke para criar uma janela de host para o controle ao criar e registrar uma classe de janela e assim por diante. No entanto, uma abordagem muito mais simples é criar uma janela com a classe de janela predefinida “estática”. Isso proporciona o procedimento de janela de que você precisa para receber notificações do controle e requer o mínimo de codificação.  
  
 O HWND do controle é exposto por meio de uma propriedade somente leitura; assim, a página de host pode usá-lo para enviar mensagens para o controle.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 O controle ListBox é criado como um filho da janela de host. A altura e a largura de ambas as janelas são definidas para os valores passados para o construtor, discutidos acima. Isso garante que o tamanho da janela de host e do controle sejam idênticos à área reservada na página.  Depois que o windows são criados, o exemplo retorna um <xref:System.Runtime.InteropServices.HandleRef> objeto que contém o HWND da janela de host.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Implementar DestroyWindow e WndProc  
 Além <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, você também deve substituir o <xref:System.Windows.Interop.HwndHost.WndProc%2A> e <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> métodos do <xref:System.Windows.Interop.HwndHost>. Neste exemplo, as mensagens para o controle são manipuladas pelo <xref:System.Windows.Interop.HwndHost.MessageHook> manipulador, assim, a implementação de <xref:System.Windows.Interop.HwndHost.WndProc%2A> e <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> é mínima. No caso de <xref:System.Windows.Interop.HwndHost.WndProc%2A>, defina `handled` para `false` para indicar que a mensagem não foi manipulada e retornar 0. Para <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, basta destruir a janela.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Hospedar o controle na página  
 Para hospedar o controle na página, você primeiro cria uma nova instância do `ControlHost` classe. Passe a altura e largura do elemento border que contém o controle (`ControlHostElement`) para o `ControlHost` construtor. Isso garante que o ListBox será dimensionado corretamente. Você, em seguida, hospede o controle na página atribuindo o `ControlHost` do objeto para o <xref:System.Windows.Controls.Decorator.Child%2A> propriedade do host <xref:System.Windows.Controls.Border>.  
  
 O exemplo anexa um manipulador para o <xref:System.Windows.Interop.HwndHost.MessageHook> eventos do `ControlHost` para receber mensagens de controle. Esse evento é gerado para cada mensagem enviada para a janela hospedada. Nesse caso, são as mensagens enviadas à janela que encapsula o verdadeiro controle ListBox, incluindo notificações do controle. O exemplo chama SendMessage para obter informações do controle e modificar seu conteúdo. Os detalhes de como a página se comunica com o controle são discutidos na próxima seção.  
  
> [!NOTE]
>  Observe que há duas declarações PInvoke para SendMessage. Isso é necessário porque uma usa a `wParam` parâmetro para passar uma cadeia de caracteres e a outra o utiliza para passar um número inteiro. Você precisa de uma declaração separada para cada assinatura a fim de garantir que o marshaling dos dados será realizado corretamente.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementar comunicação entre o controle e a página  
 Você pode manipular o controle, enviando-as mensagens do Windows. Para notificar você de que o usuário interagiu com ele, o controle envia notificações para a janela de host. O [hospedando um controle Win32 ListBox no WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) exemplo inclui uma interface do usuário que fornece vários exemplos de como isso funciona:  
  
-   Acrescentar um novo item à lista.  
  
-   Excluir o item selecionado da lista  
  
-   Exibir o texto do item selecionado atualmente.  
  
-   Exibir o número de itens na lista.  
  
 O usuário também pode selecionar um item na caixa de listagem clicando sobre ele, como faria para um aplicativo Win32 convencional. Os dados exibidos são atualizados sempre que o usuário altera o estado da caixa de listagem ao selecionar, adicionar ou acrescentar um item.  
  
 Para acrescentar itens, enviar a caixa de listagem uma [ `LB_ADDSTRING` mensagem](/windows/desktop/Controls/lb-addstring). Para excluir itens, envie [ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel) para obter o índice da seleção atual e, em seguida [ `LB_DELETESTRING` ](/windows/desktop/Controls/lb-deletestring) para excluir o item. O exemplo também envia [ `LB_GETCOUNT` ](/windows/desktop/Controls/lb-getcount)e usa o valor retornado para atualizar a exibição que mostra o número de itens. Ambas as instâncias de [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) usar uma das declarações PInvoke discutidas na seção anterior.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Quando o usuário seleciona um item ou alterando sua seleção, o controle notifica a janela do host, enviando-as uma [ `WM_COMMAND` mensagem](/windows/desktop/menurc/wm-command), que gera o <xref:System.Windows.Interop.HwndHost.MessageHook> evento para a página. O manipulador recebe as mesmas informações que o procedimento de janela principal da janela de host. Ele também passa uma referência a um valor booliano, `handled`. Você definir `handled` para `true` para indicar que manipulou a mensagem e nenhum processamento adicional é necessária.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command) é enviado para uma variedade de motivos, portanto, você deve examinar a ID de notificação para determinar se ele é um evento que você deseja manipular. A ID está contida na palavra alta da `wParam` parâmetro. O exemplo usa operadores bit a bit para extrair a ID. Se o usuário tiver feito ou alterado sua seleção, a ID será [ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange).  
  
 Quando [ `LBN_SELCHANGE` ](https://msdn.microsoft.com/library/windows/desktop/bb775161(v=vs.85).aspx) é recebida, o exemplo obtém o índice do item selecionado, enviando o controle de uma [ `LB_GETCURSEL` mensagem](/windows/desktop/Controls/lb-getcursel). Para obter o texto, você primeiro crie um <xref:System.Text.StringBuilder>. Você envia, em seguida, o controle de um [ `LB_GETTEXT` mensagem](/windows/desktop/Controls/lb-gettext). Passe a esvaziar <xref:System.Text.StringBuilder> objeto como o `wParam` parâmetro. Quando [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) retorna, o <xref:System.Text.StringBuilder> conterá o texto do item selecionado. Esse uso de [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) exige outra declaração de PInvoke.  
  
 Por fim, defina `handled` para `true` para indicar que a mensagem foi tratada.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Interop.HwndHost>
- [Interoperação do WPF e do Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
- [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
