---
title: 'Passo a passo: hospedar um controle Win32 no WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: cc27189afd2185d5f0a1eeacccf4c537dd3d9c2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917537"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Passo a passo: hospedar um controle Win32 no WPF
O Windows Presentation Foundation (WPF) fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento substancial no código Win32, pode ser mais eficiente reutilizar pelo menos um pouco esse código em seu aplicativo WPF em vez de reescrevê-lo completamente. O WPF fornece um mecanismo direto para hospedar uma janela do Win32, em uma página do WPF.  
  
 Este tópico orienta você por um aplicativo, [hospedando um controle ListBox do Win32 no exemplo do WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), que hospeda um controle de caixa de listagem do Win32. Esse procedimento geral pode ser estendido para hospedar qualquer janela Win32.  

<a name="requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Este tópico pressupõe uma familiaridade básica com a programação do WPF e da API do Windows. Para obter uma introdução básica à programação do WPF, consulte [introdução](../getting-started/index.md). Para obter uma introdução à programação da API do Windows, confira qualquer um dos vários livros sobre o assunto, em particular, as *janelas de programação* , de Charles Petzold.  
  
 Como o exemplo que acompanha este tópico é implementado no C#, ele faz uso de PInvoke (serviços de invocação de plataforma) para acessar a API do Windows. Alguma familiaridade com o PInvoke é útil, mas não essencial.  
  
> [!NOTE]
> Este tópico inclui alguns exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Você pode obter ou exibir o código completo da [Hospedagem de um controle ListBox do Win32 no exemplo do WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>O procedimento básico  
 Esta seção descreve o procedimento básico para hospedar uma janela do Win32 em uma página do WPF. As seções restantes apresentam detalhes de cada etapa.  
  
 O procedimento básico de hospedagem é:  
  
1. Implemente uma página do WPF para hospedar a janela. Uma técnica é criar um <xref:System.Windows.Controls.Border> elemento para reservar uma seção da página para a janela hospedada.  
  
2. Implemente uma classe para hospedar o controle que herda <xref:System.Windows.Interop.HwndHost>de.  
  
3. Nessa classe, substitua o membro <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>da classe.  
  
4. Crie a janela hospedada como um filho da janela que contém a página do WPF. Embora a programação do WPF convencional não precise usá-la explicitamente, a página de hospedagem é uma janela com um identificador (HWND). Você recebe a página HWND por meio `hwndParent` do parâmetro <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> do método. A janela hospedada deve ser criada como um filho desse HWND.  
  
5. Depois de criar a janela do host, retorne o HWND da janela hospedada. Se você quiser hospedar um ou mais controles do Win32, você normalmente criará uma janela de host como um filho do HWND e tornará os controles filhos dessa janela do host. Encapsular os controles em uma janela de host fornece uma maneira simples de sua página do WPF receber notificações dos controles, que lida com alguns problemas específicos do Win32 com notificações entre o limite de HWND.  
  
6. Manipule as mensagens selecionadas enviadas à janela de host, como notificações dos controles filho. Há duas formas de fazer isso.  
  
    - Se você preferir manipular mensagens em sua classe de hospedagem, substitua o <xref:System.Windows.Interop.HwndHost.WndProc%2A> método <xref:System.Windows.Interop.HwndHost> da classe.  
  
    - Se você preferir que o WPF Manipule as mensagens, manipule o <xref:System.Windows.Interop.HwndHost> evento de classe <xref:System.Windows.Interop.HwndHost.MessageHook> em seu code-behind. Esse evento ocorre para cada mensagem recebida pela janela hospedada. Se você escolher essa opção, ainda deverá substituir <xref:System.Windows.Interop.HwndHost.WndProc%2A>, mas precisará apenas de uma implementação mínima.  
  
7. Substitua os <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> métodos <xref:System.Windows.Interop.HwndHost.WndProc%2A> e de <xref:System.Windows.Interop.HwndHost>. Você deve substituir esses métodos para atender ao <xref:System.Windows.Interop.HwndHost> contrato, mas você pode precisar apenas fornecer uma implementação mínima.  
  
8. No arquivo code-behind, crie uma instância da classe de Hospedagem de controle e torne-a um filho do <xref:System.Windows.Controls.Border> elemento que se destina a hospedar a janela.  
  
9. Comunique-se com a janela hospedada [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] enviando mensagens de ti e manipulando mensagens de suas janelas filhas, como notificações enviadas por controles.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementar o layout da página  
 O layout da página do WPF que hospeda o controle ListBox consiste em duas regiões. O lado esquerdo da página hospeda vários controles WPF que fornecem um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] que permite que você manipule o controle Win32. O canto superior direito da página tem uma região quadrada para o controle ListBox hospedado.  
  
 O código para implementar esse layout é bem simples. O elemento raiz é um <xref:System.Windows.Controls.DockPanel> que tem dois elementos filho. O primeiro é um <xref:System.Windows.Controls.Border> elemento que hospeda o controle ListBox. Ele ocupa um quadrado de 200x200 no canto superior direito da página. O segundo é um <xref:System.Windows.Controls.StackPanel> elemento que contém um conjunto de controles WPF que exibem informações e permitem que você manipule o controle ListBox Definindo Propriedades de interoperação expostas. Para cada um dos elementos que são filhos do <xref:System.Windows.Controls.StackPanel>, consulte o material de referência para os vários elementos usados para obter detalhes sobre o que esses elementos são ou o que eles fazem, eles são listados no código de exemplo abaixo, mas não serão explicados aqui (o básico o modelo de interoperação não requer nenhum deles, eles são fornecidos para adicionar alguma interatividade ao exemplo).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementar uma classe para hospedar o controle Microsoft Win32  
 O núcleo dessa amostra é a classe que realmente hospeda o controle: ControlHost.cs. Herda de <xref:System.Windows.Interop.HwndHost>. O construtor usa dois parâmetros, altura e largura, que correspondem à altura e à largura do <xref:System.Windows.Controls.Border> elemento que hospeda o controle ListBox. Esses valores são usados posteriormente para garantir que o tamanho do controle corresponda ao <xref:System.Windows.Controls.Border> elemento.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Também existe um conjunto de constantes. Essas constantes são amplamente obtidas de WinUser. h e permitem que você use nomes convencionais ao chamar funções do Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Substituir o BuildWindowCore para criar a janela do Microsoft Win32  
 Você substitui esse método para criar a janela do Win32 que será hospedada pela página e fará a conexão entre a janela e a página. Como essa amostra envolve a hospedagem de um controle ListBox, duas janelas são criadas. A primeira é a janela que é realmente hospedada pela página do WPF. O controle ListBox é criado como um filho dessa janela.  
  
 A razão para essa abordagem é simplificar o processo de recebimento de notificações do controle. A <xref:System.Windows.Interop.HwndHost> classe permite processar as mensagens enviadas para a janela que está hospedando. Se você hospedar um controle Win32 diretamente, receberá as mensagens enviadas para o loop de mensagem interno do controle. É possível exibir o controle e lhe enviar mensagens, mas você não receberá as notificações que o controle envia para a janela pai. Isso significa, entre outras coisas, que você não tem nenhuma maneira de detectar quando o usuário interage com o controle. Em vez disso, crie uma janela de host e transforme o controle em filho dessa janela. Assim, pode processar as mensagens para a janela de host, incluindo as notificações enviadas a ela pelo controle. Por uma questão de conveniência, como a janela de host é mais que um wrapper simples para o controle, o pacote será chamado de controle ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Criar a janela de host e o controle ListBox  
 Você pode usar o PInvoke para criar uma janela de host para o controle criando e registrando uma classe de janela e assim por diante. No entanto, uma abordagem muito mais simples é criar uma janela com a classe de janela predefinida “estática”. Isso proporciona o procedimento de janela de que você precisa para receber notificações do controle e requer o mínimo de codificação.  
  
 O HWND do controle é exposto por meio de uma propriedade somente leitura; assim, a página de host pode usá-lo para enviar mensagens para o controle.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 O controle ListBox é criado como um filho da janela de host. A altura e a largura de ambas as janelas são definidas para os valores passados para o construtor, discutidos acima. Isso garante que o tamanho da janela de host e do controle sejam idênticos à área reservada na página.  Depois que as janelas são criadas, o exemplo retorna <xref:System.Runtime.InteropServices.HandleRef> um objeto que contém o HWND da janela do host.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Implementar DestroyWindow e WndProc  
 Além <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>disso, você também deve substituir os <xref:System.Windows.Interop.HwndHost.WndProc%2A> métodos e <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> do <xref:System.Windows.Interop.HwndHost>. Neste exemplo, as mensagens para o controle são tratadas pelo <xref:System.Windows.Interop.HwndHost.MessageHook> manipulador, portanto, a implementação de <xref:System.Windows.Interop.HwndHost.WndProc%2A> e <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> é mínima. No caso de <xref:System.Windows.Interop.HwndHost.WndProc%2A>, defina `handled` como `false` para indicar que a mensagem não foi tratada e retornou 0. Para <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>o, basta destruir a janela.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Hospedar o controle na página  
 Para hospedar o controle na página, você primeiro cria uma nova instância da `ControlHost` classe. Passe a altura e a largura do elemento Border que contém o controle (`ControlHostElement`) para o `ControlHost` Construtor. Isso garante que o ListBox será dimensionado corretamente. Em seguida, você hospeda o controle na página atribuindo o `ControlHost` objeto <xref:System.Windows.Controls.Decorator.Child%2A> à propriedade do host <xref:System.Windows.Controls.Border>.  
  
 O exemplo anexa um manipulador ao <xref:System.Windows.Interop.HwndHost.MessageHook> evento `ControlHost` do para receber mensagens do controle. Esse evento é gerado para cada mensagem enviada para a janela hospedada. Nesse caso, são as mensagens enviadas à janela que encapsula o verdadeiro controle ListBox, incluindo notificações do controle. O exemplo chama SendMessage para obter informações do controle e modificar seu conteúdo. Os detalhes de como a página se comunica com o controle são discutidos na próxima seção.  
  
> [!NOTE]
> Observe que há duas declarações PInvoke para SendMessage. Isso é necessário porque um usa o `wParam` parâmetro para passar uma cadeia de caracteres e a outra usa-o para passar um inteiro. Você precisa de uma declaração separada para cada assinatura a fim de garantir que o marshaling dos dados será realizado corretamente.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementar comunicação entre o controle e a página  
 Você manipula o controle enviando mensagens do Windows. Para notificar você de que o usuário interagiu com ele, o controle envia notificações para a janela de host. O exemplo de [Hospedagem de um controle ListBox do Win32 no WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) inclui uma interface do usuário que fornece vários exemplos de como isso funciona:  
  
- Acrescentar um novo item à lista.  
  
- Excluir o item selecionado da lista  
  
- Exibir o texto do item selecionado atualmente.  
  
- Exibir o número de itens na lista.  
  
 O usuário também pode selecionar um item na caixa de listagem clicando nele, assim como faria para um aplicativo Win32 convencional. Os dados exibidos são atualizados sempre que o usuário altera o estado da caixa de listagem ao selecionar, adicionar ou acrescentar um item.  
  
 Para acrescentar itens, envie uma [ `LB_ADDSTRING` mensagem](/windows/desktop/Controls/lb-addstring)à caixa de listagem. Para excluir itens, envie [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) para obter o índice da seleção atual e, em [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) seguida, para excluir o item. O exemplo também envia [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)e usa o valor retornado para atualizar a exibição que mostra o número de itens. Ambas as instâncias do [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) usam uma das declarações PInvoke discutidas na seção anterior.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Quando o usuário seleciona um item ou altera sua seleção, o controle notifica a janela do host enviando uma [ `WM_COMMAND` mensagem](/windows/desktop/menurc/wm-command), o que gera o <xref:System.Windows.Interop.HwndHost.MessageHook> evento para a página. O manipulador recebe as mesmas informações que o procedimento de janela principal da janela de host. Ele também passa uma referência a um valor booliano `handled`,. Você define `handled` como `true` para indicar que você tratou a mensagem e nenhum processamento adicional é necessário.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)é enviado por vários motivos, portanto, você deve examinar a ID de notificação para determinar se é um evento que você deseja manipular. A ID está contida na palavra alta do `wParam` parâmetro. O exemplo usa operadores de bit-a-bit para extrair a ID. Se o usuário tiver feito ou alterado sua seleção, a ID será [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange).  
  
 Quando [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) é recebido, o exemplo obtém o índice do item selecionado enviando ao controle uma [ `LB_GETCURSEL` mensagem](/windows/desktop/Controls/lb-getcursel). Para obter o texto, primeiro crie um <xref:System.Text.StringBuilder>. Em seguida, você envia ao controle uma [ `LB_GETTEXT` mensagem](/windows/desktop/Controls/lb-gettext). Passe o objeto <xref:System.Text.StringBuilder> vazio como o `wParam` parâmetro. Quando [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) retorna, o <xref:System.Text.StringBuilder> conterá o texto do item selecionado. Esse uso de [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) requer ainda outra declaração PInvoke.  
  
 Por fim, `handled` defina `true` como para indicar que a mensagem foi tratada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Interop.HwndHost>
- [Interoperação do WPF e do Win32](wpf-and-win32-interoperation.md)
- [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
