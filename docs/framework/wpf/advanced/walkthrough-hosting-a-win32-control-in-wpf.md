---
title: "Instruções passo a passo: hospedando um controle Win32 no WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 566be72cf330f6da83987f5e693176552471f091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Instruções passo a passo: hospedando um controle Win32 no WPF
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento significativo em [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] código, pode ser mais eficiente reutilizar pelo menos parte desse código em seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo em vez de reescrevê-la completamente. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Fornece um mecanismo simples para hospedar uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela, em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página.  
  
 Este tópico orienta você por meio de um aplicativo, [hospedando um controle ListBox de Win32 no exemplo do WPF](http://go.microsoft.com/fwlink/?LinkID=159998), que hospeda um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controle caixa de listagem. Esse procedimento geral pode ser estendido para hospedar qualquer [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela.  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Este tópico pressupõe uma familiaridade básica com ambos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de programação. Para obter uma introdução básica [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de programação, consulte [Introdução](../../../../docs/framework/wpf/getting-started/index.md). Para obter uma introdução ao [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de programação, consulte qualquer dos numerosos livros no assunto, em particular *Programming Windows* por Charles Petzold.  
  
 Como o exemplo que acompanha este tópico é implementado no [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], ele faz uso de [!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)] para acessar o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Familiaridade com [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] é útil, mas não essenciais.  
  
> [!NOTE]
>  Este tópico inclui alguns exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Você pode obter ou exibir o código completo de [hospedando um controle ListBox de Win32 no exemplo do WPF](http://go.microsoft.com/fwlink/?LinkID=159998).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>O procedimento básico  
 Esta seção descreve o procedimento básico para hospedar uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página. As seções restantes apresentam detalhes de cada etapa.  
  
 O procedimento básico de hospedagem é:  
  
1.  Implementar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página para hospedar a janela. Uma técnica é criar um <xref:System.Windows.Controls.Border> elemento para reservar uma seção da página para a janela hospedada.  
  
2.  Implementar uma classe para hospedar o controle que herda de <xref:System.Windows.Interop.HwndHost>.  
  
3.  Nessa classe, substituir o <xref:System.Windows.Interop.HwndHost> membro de classe <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4.  Crie a janela hospedada como um filho da janela que contém o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página. Embora convencional [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programação não precisa fazer explicitamente usá-lo, a página de hospedagem é uma janela com um identificador (HWND). Você recebe o HWND da página por meio de `hwndParent` parâmetro do <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> método. A janela hospedada deve ser criada como um filho desse HWND.  
  
5.  Depois de criar a janela do host, retorne o HWND da janela hospedada. Se você quiser hospedar um ou mais [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controles, você normalmente cria uma janela de host como um filho do HWND e verifique os filhos de controles de janela host. Envolver os controles em uma janela host fornece uma maneira simples para seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página para receber notificações dos controles, que lida com algumas particular [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problemas de notificações que cruzam o limite HWND.  
  
6.  Manipule as mensagens selecionadas enviadas à janela de host, como notificações dos controles filho. Há duas formas de fazer isso.  
  
    -   Se você preferir tratar mensagens em sua classe de hospedagem, substitua o <xref:System.Windows.Interop.HwndHost.WndProc%2A> método o <xref:System.Windows.Interop.HwndHost> classe.  
  
    -   Se você preferir que o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tratar as mensagens, trate o <xref:System.Windows.Interop.HwndHost> classe <xref:System.Windows.Interop.HwndHost.MessageHook> eventos em seu code-behind. Esse evento ocorre para cada mensagem recebida pela janela hospedada. Se você escolher essa opção, você ainda deve substituir <xref:System.Windows.Interop.HwndHost.WndProc%2A>, mas você só precisa de uma implementação mínima.  
  
7.  Substituir o <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> e <xref:System.Windows.Interop.HwndHost.WndProc%2A> métodos de <xref:System.Windows.Interop.HwndHost>. Você deve substituir esses métodos para satisfazer o <xref:System.Windows.Interop.HwndHost> contrato, mas você só precisará fornecer uma implementação mínima.  
  
8.  No seu arquivo de code-behind, crie uma instância da classe que hospeda controles e torná-lo um filho de <xref:System.Windows.Controls.Border> elemento que é destinado a hospedar a janela.  
  
9. Se comunicar com a janela hospedada enviando- [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] mensagens e manipulação de janelas filho, como notificações enviadas por controles.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementar o layout da página  
 O layout para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página que hospeda o controle ListBox consiste em duas regiões. O lado esquerdo da página hospeda vários [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles que oferecem um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] que permite que você manipule o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controle. O canto superior direito da página tem uma região quadrada para o controle ListBox hospedado.  
  
 O código para implementar este layout é muito simple. O elemento raiz é um <xref:System.Windows.Controls.DockPanel> que tem dois elementos filho. A primeira é uma <xref:System.Windows.Controls.Border> elemento que hospeda o controle ListBox. Ele ocupa um quadrado de 200x200 no canto superior direito da página. O segundo é um <xref:System.Windows.Controls.StackPanel> elemento que contém um conjunto de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles que exibem informações e permitem que você manipule o controle ListBox definindo expostos propriedades de interoperação. Para cada um dos elementos que são filhos do <xref:System.Windows.Controls.StackPanel>, consulte o material de referência para os vários elementos usados para obter detalhes sobre quais são esses elementos ou o que fazer, eles estão listados no código de exemplo abaixo, mas não serão explicados aqui (o básico modelo de interoperação não requer nenhum deles, eles são fornecidos para adicionar alguma interatividade ao exemplo).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementar uma classe para hospedar o controle Microsoft Win32  
 O núcleo dessa amostra é a classe que realmente hospeda o controle: ControlHost.cs. Ele herda de <xref:System.Windows.Interop.HwndHost>. O construtor usa dois parâmetros, altura e largura, que correspondem à altura e a largura do <xref:System.Windows.Controls.Border> elemento que hospeda o controle ListBox. Esses valores são usados mais tarde para garantir que o tamanho do controle corresponda a <xref:System.Windows.Controls.Border> elemento.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Também existe um conjunto de constantes. Essas constantes são basicamente extraídas de WinUser. h e permitem que você use nomes convencionais ao chamar [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funções.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Substituir o BuildWindowCore para criar a janela do Microsoft Win32  
 Você substitui esse método para criar o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela que será hospedada pela página e fazer a conexão entre a janela e a página. Como essa amostra envolve a hospedagem de um controle ListBox, duas janelas são criadas. A primeira é a janela que é realmente hospedada pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página. O controle ListBox é criado como um filho dessa janela.  
  
 A razão para essa abordagem é simplificar o processo de recebimento de notificações do controle. O <xref:System.Windows.Interop.HwndHost> classe permite que você processe as mensagens enviadas para a janela que está hospedando. Se você hospedar um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controlar diretamente, você receberá as mensagens enviadas para o loop de mensagem interno do controle. É possível exibir o controle e lhe enviar mensagens, mas você não receberá as notificações que o controle envia para a janela pai. Isso significa, entre outras coisas, que você não tem nenhuma maneira de detectar quando o usuário interage com o controle. Em vez disso, crie uma janela de host e transforme o controle em filho dessa janela. Assim, pode processar as mensagens para a janela de host, incluindo as notificações enviadas a ela pelo controle. Por uma questão de conveniência, como a janela de host é mais que um wrapper simples para o controle, o pacote será chamado de controle ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Criar a janela de host e o controle ListBox  
 Você pode usar [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] para criar uma janela do host para o controle ao criar e registrar uma classe de janela e assim por diante. No entanto, uma abordagem muito mais simples é criar uma janela com a classe de janela predefinida “estática”. Isso proporciona o procedimento de janela de que você precisa para receber notificações do controle e requer o mínimo de codificação.  
  
 O HWND do controle é exposto por meio de uma propriedade somente leitura; assim, a página de host pode usá-lo para enviar mensagens para o controle.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 O controle ListBox é criado como um filho da janela de host. A altura e a largura de ambas as janelas são definidas para os valores passados para o construtor, discutidos acima. Isso garante que o tamanho da janela de host e do controle sejam idênticos à área reservada na página.  Depois que o windows são criados, o exemplo retorna um <xref:System.Runtime.InteropServices.HandleRef> objeto que contém o HWND da janela do host.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Implementar DestroyWindow e WndProc  
 Além <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, você também deve substituir o <xref:System.Windows.Interop.HwndHost.WndProc%2A> e <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> métodos do <xref:System.Windows.Interop.HwndHost>. Neste exemplo, as mensagens para o controle são tratadas pelo <xref:System.Windows.Interop.HwndHost.MessageHook> manipulador, assim, a implementação de <xref:System.Windows.Interop.HwndHost.WndProc%2A> e <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> é mínimo. No caso de <xref:System.Windows.Interop.HwndHost.WndProc%2A>, defina `handled` para `false` para indicar que a mensagem não foi tratada e retorne 0. Para <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, simplesmente destruir a janela.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Hospedar o controle na página  
 Para hospedar o controle na página, primeiro crie uma nova instância do `ControlHost` classe. Passe a altura e largura do elemento de borda que contém o controle (`ControlHostElement`) para o `ControlHost` construtor. Isso garante que o ListBox será dimensionado corretamente. Você então hospeda o controle na página atribuindo o `ControlHost` o objeto para o <xref:System.Windows.Controls.Decorator.Child%2A> propriedade do host <xref:System.Windows.Controls.Border>.  
  
 O exemplo anexa um manipulador para o <xref:System.Windows.Interop.HwndHost.MessageHook> eventos do `ControlHost` para receber mensagens de controle. Esse evento é gerado para cada mensagem enviada para a janela hospedada. Nesse caso, são as mensagens enviadas à janela que encapsula o verdadeiro controle ListBox, incluindo notificações do controle. O exemplo chama SendMessage para obter informações do controle e modificar seu conteúdo. Os detalhes de como a página se comunica com o controle são discutidos na próxima seção.  
  
> [!NOTE]
>  Observe que há dois [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] declarações para SendMessage. Isso é necessário porque uma usa a `wParam` parâmetro para passar uma cadeia de caracteres e o outro usa para passar um número inteiro. Você precisa de uma declaração separada para cada assinatura a fim de garantir que o marshaling dos dados será realizado corretamente.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementar comunicação entre o controle e a página  
 Manipular o controle enviando- [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] mensagens. Para notificar você de que o usuário interagiu com ele, o controle envia notificações para a janela de host. O [hospedando um controle ListBox de Win32 no exemplo do WPF](http://go.microsoft.com/fwlink/?LinkID=159998) exemplo inclui uma interface do usuário que fornece vários exemplos de como isso funciona:  
  
-   Acrescentar um novo item à lista.  
  
-   Excluir o item selecionado da lista  
  
-   Exibir o texto do item selecionado atualmente.  
  
-   Exibir o número de itens na lista.  
  
 O usuário também pode selecionar um item na caixa de listagem clicando nele, como faria para um convencional [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo. Os dados exibidos são atualizados sempre que o usuário altera o estado da caixa de listagem ao selecionar, adicionar ou acrescentar um item.  
  
 Para acrescentar itens, envie uma mensagem LB_ADDSTRING à caixa de listagem. Para excluir itens, envie LB_GETCURSEL para obter o índice da seleção atual e, em seguida, LB_DELETESTRING para excluir o item. A amostra também envia LB_GETCOUNT e utiliza o valor retornado para atualizar a exibição que mostra o número de itens. Ambas as essas instâncias de SendMessage usam uma da [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] declarações discutidas na seção anterior.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Quando o usuário seleciona um item ou altera sua seleção, o controle notifica a janela do host ao enviar uma mensagem WM_COMMAND, que gera o <xref:System.Windows.Interop.HwndHost.MessageHook> evento para a página. O manipulador recebe as mesmas informações que o procedimento de janela principal da janela de host. Ele também passa uma referência a um valor booliano, `handled`. Definir `handled` para `true` para indicar que você tratou a mensagem e nenhum processamento adicional é necessária.  
  
 O WM_COMMAND é enviado por várias razões; portanto, você precisa examinar a ID da notificação para determinar se é um evento que deseja manipular. A identificação está contida na palavra alta da `wParam` parâmetro. Como [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] does não tem uma macro HIWORD, o exemplo usa operadores bit a bit para extrair a identificação. Se o usuário tiver feito ou alterado sua seleção, a ID será LBN_SELCHANGE.  
  
 Quando a LBN_SELCHANGE é recebida, a amostra obtém o índice do item selecionado mediante o envio de uma mensagem LB_GETCURSEL para o controle. Para obter o texto, você primeiro crie um <xref:System.Text.StringBuilder>. A seguir, envia uma mensagem LB_GETTEXT para o controle. Passar vazio <xref:System.Text.StringBuilder> de objeto como o `wParam` parâmetro. Quando SendMessage retornar, o <xref:System.Text.StringBuilder> conterá o texto do item selecionado. Esse uso de SendMessage requer ainda outra [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] declaração.  
  
 Finalmente, defina `handled` para `true` para indicar que a mensagem foi tratada.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Interop.HwndHost>  
 [Interoperação do WPF e do Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
