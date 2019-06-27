---
title: Visão geral das caixas de diálogo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: 8008feb91a72353a74a647cf79bcecbf7023f962
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410551"
---
# <a name="dialog-boxes-overview"></a>Visão geral das caixas de diálogo
Aplicativos autônomos geralmente têm uma janela principal que exibe os principais dados sobre os quais o aplicativo opera e expõe a funcionalidade para processar os dados por meio de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mecanismos, como barras de menus, barras de ferramentas e barras de status. Um aplicativo não trivial também pode exibir janelas adicionais para fazer o seguinte:  
  
- Exibir informações específicas aos usuários.  
  
- Coletar informações de usuários.  
  
- Exibir e coletar informações.  
  
 Esses tipos de janelas são conhecidos como *caixas de diálogo*, e há dois tipos: restrita e sem janela restrita.  
  
 Um *modal* caixa de diálogo é exibida por uma função quando a função precisa de dados adicionais de um usuário para continuar. Como a função depende da caixa de diálogo modal para coletar dados, a caixa de diálogo modal também impede que um usuário ative outras janelas no aplicativo enquanto ele está aberto. Na maioria dos casos, uma caixa de diálogo modal permite que o usuário sinalize quando ele tiver terminado a caixa de diálogo modal pressionando um **Okey** ou **Cancelar** botão. Pressionar o **Okey** botão indica que um usuário inseriu dados e deseja que a função continue o processamento com esses dados. Pressionar o **Cancelar** botão indica que um usuário deseja parar a função de execução totalmente. Os exemplos de caixas de diálogo modais mais comuns são mostrados para abrir, salvar e imprimir dados.  
  
 Um *sem janela restrita* caixa de diálogo, por outro lado, não impede que um usuário ative outras janelas enquanto ele está aberto. Por exemplo, se um usuário desejar localizar ocorrências de uma palavra específica em um documento, uma janela principal geralmente abrirá uma caixa de diálogo para solicitar a um usuário qual palavra ele está procurando. No entanto, como a localização de uma palavra não impede que um usuário edite o documento, a caixa de diálogo não precisa ser restrita. Uma caixa de diálogo sem janela restrita fornece pelo menos um **feche** botão para fechar a caixa de diálogo e pode fornecer outros botões para executar funções específicas, como um **Localizar próximo** botão para localizar a próxima palavra que corresponde a critérios de localização de uma pesquisa de palavra.  
  
 Windows Presentation Foundation (WPF) permite que você crie vários tipos de caixas de diálogo, incluindo caixas de mensagem, caixas de diálogo comuns e caixas de diálogo personalizadas. Este tópico aborda cada um e o [amostra de caixa de diálogo](https://go.microsoft.com/fwlink/?LinkID=159984) fornece os exemplos correspondentes.  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Caixas de mensagem  
 Um *caixa de mensagem* é uma caixa de diálogo que pode ser usada para exibir informações textuais e permitir que os usuários tomem decisões com botões. A figura a seguir mostra uma caixa de mensagem que exibe informações textuais, faz uma pergunta e fornece ao usuário três botões para responder à pergunta.  
  
 ![Uma caixa de diálogo do processador do Word perguntando se você deseja salvar as alterações no documento antes que o aplicativo é fechado.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Para criar uma caixa de mensagem, use o <xref:System.Windows.MessageBox> classe. <xref:System.Windows.MessageBox> permite que você configure o texto da caixa de mensagem, título, ícone e botões, usando código semelhante ao seguinte.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Para mostrar uma caixa de mensagem, você chama o `static` <xref:System.Windows.MessageBox.Show%2A> método, conforme demonstrado no código a seguir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Quando o código que mostra uma caixa de mensagem precisa detectar e processar a decisão do usuário (qual botão foi pressionado), o código pode inspecionar o resultado da caixa de mensagem, conforme mostrado no código a seguir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Para obter mais informações sobre como usar caixas de mensagem, consulte <xref:System.Windows.MessageBox>, [amostra de MessageBox](https://go.microsoft.com/fwlink/?LinkID=160023), e [amostra de caixa de diálogo](https://go.microsoft.com/fwlink/?LinkID=159984).  
  
 Embora <xref:System.Windows.MessageBox> podem oferecer uma experiência de usuário de caixa de diálogo simples, a vantagem de usar <xref:System.Windows.MessageBox> é o que é o único tipo de janela que pode ser mostrado por aplicativos que são executados em uma área restrita de confiança parcial (consulte [segurança](../security-wpf.md)), como [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 A maioria das caixas de diálogo exibe e coleta dados mais complexos que o resultado de uma caixa de mensagem, incluindo texto, seleção (caixas de seleção), seleção mutuamente exclusiva (botões de opção) e seleção de lista (caixas de listagem, caixas de combinação, caixas de listagem suspensas). Nesses casos, o Windows Presentation Foundation (WPF) fornece várias caixas de diálogo comuns e permite que você crie suas próprias caixas de diálogo, embora o uso seja limitado aos aplicativos executados com confiança total.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Caixas de diálogo comuns  
 O [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] implementa uma variedade de caixas de diálogo reutilizáveis que são comuns a todos os aplicativos, incluindo caixas de diálogo Abrir Arquivo, Salvar Arquivo e Imprimir. Como essas caixas de diálogo são implementadas pelo sistema operacional, elas podem ser compartilhadas entre todos os aplicativos executados no sistema operacional, o que ajuda na consistência da experiência do usuário. Quando os usuários estiverem familiarizados com o uso de uma caixa de diálogo fornecida pelo sistema operacional em um aplicativo, eles não precisarão aprender a usar a caixa de diálogo em outros aplicativos. Porque essas caixas de diálogo estão disponíveis para todos os aplicativos e como elas ajudam a fornecer uma experiência de usuário consistente, elas são conhecidas como *caixas de diálogo comuns*.  
  
 Windows Presentation Foundation (WPF) encapsula o arquivo aberto, salve o arquivo e caixas de diálogo comuns de impressão e as expõe como classes gerenciadas para uso em aplicativos autônomos. Este tópico fornece uma visão geral breve de cada uma delas.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Caixa de diálogo Abrir arquivo  
 A caixa de diálogo Abrir Arquivo, mostrada na figura a seguir, é usada pela funcionalidade de abertura de arquivo para recuperar o nome de um arquivo a ser aberto.  
  
 ![Uma caixa de diálogo Abrir mostrando o local para recuperar o arquivo.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 A caixa de diálogo comum Abrir arquivo é implementada como o <xref:Microsoft.Win32.OpenFileDialog> de classe e está localizado no <xref:Microsoft.Win32> namespace. O código a seguir mostra como criar, configurar e mostrar uma e como processar o resultado.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Para obter mais informações sobre a caixa de diálogo Abrir arquivo, consulte <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> pode ser usado para recuperar os nomes de arquivo com segurança por aplicativos executados com confiança parcial (consulte [segurança](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>caixa de diálogo Salvar Arquivo  
 A caixa de diálogo Salvar Arquivo, mostrada na figura a seguir, é usada pela funcionalidade de salvamento de arquivo para recuperar o nome de um arquivo a ser salvo.  
  
 ![Salvar como caixa de diálogo que mostra o local para salvar o arquivo.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Salvar da caixa de diálogo de arquivo comum é implementado como o <xref:Microsoft.Win32.SaveFileDialog> classe e está localizado no <xref:Microsoft.Win32> namespace. O código a seguir mostra como criar, configurar e mostrar uma e como processar o resultado.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Para obter mais informações sobre a salvar arquivos da caixa de diálogo, consulte <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>caixa de diálogo Imprimir

A caixa de diálogo Imprimir, mostrada na figura a seguir, é usada pela funcionalidade de impressão para escolher e configurar a impressora na qual um usuário deseja imprimir os dados.  
  
![Captura de tela que mostra uma caixa de diálogo de impressão.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
A caixa de diálogo de impressão comum é implementada como o <xref:System.Windows.Controls.PrintDialog> classe e está localizado no <xref:System.Windows.Controls> namespace. O código a seguir mostra como criar, configurar e mostrar uma.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Para obter mais informações sobre a caixa de diálogo de impressão, consulte <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Para obter uma discussão detalhada de impressão no WPF, consulte [visão geral sobre impressão](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Caixas de diálogo personalizadas

Embora as caixas de diálogo comuns sejam úteis e devam ser usadas quando possível, elas não dão suporte aos requisitos de caixas de diálogo específicas ao domínio. Nesses casos, você precisa criar suas próprias caixas de diálogo. Como veremos, uma caixa de diálogo é uma janela com comportamentos especiais. <xref:System.Windows.Window> implementa esses comportamentos e, consequentemente, você usará <xref:System.Windows.Window> para criar caixas de diálogo modais e sem janela restrita personalizadas.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Criando uma caixa de diálogo personalizada restrita

Este tópico mostra como usar <xref:System.Windows.Window> para criar uma implementação de caixa de diálogo modal típica, usando o `Margins` caixa de diálogo como um exemplo (consulte [amostra de caixa de diálogo](https://go.microsoft.com/fwlink/?LinkID=159984)). O `Margins` caixa de diálogo é mostrada na figura a seguir.  
  
 ![Uma caixa de diálogo margens com campos para definir a margem esquerda, a margem superior, a margem direita e a margem inferior.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Configurando uma caixa de diálogo modal

A interface do usuário de uma caixa de diálogo típica inclui o seguinte:  
  
- Os vários controles que são necessários para coletar os dados desejados.  
  
- Uma **Okey** botão que os usuários clicam para fechar a caixa de diálogo, volte para a função e continuam o processamento.  
  
- Um **Cancelar** botão que os usuários clicam para fechar a caixa de diálogo e parar a processamento da função.  
  
- Um **fechar** botão na barra de título.  
  
- Um ícone.  
  
- **Minimizar**, **maximizar**, e **restaurar** botões.  
  
- Um **sistema** menu para minimizar, maximizar, restaurar e fechar a caixa de diálogo.  
  
- Uma posição acima e no centro da janela que abriu a caixa de diálogo.  
  
- A capacidade de ser redimensionadas sempre que possível para impedir que a caixa de diálogo seja muito pequeno e para fornecer ao usuário com um tamanho padrão útil. Isso exige que você defina o padrão e uma dimensões mínimas.  
  
- A tecla ESC como um atalho de teclado que faz com que o **Cancelar** botão seja pressionado. Você pode fazer isso definindo a <xref:System.Windows.Controls.Button.IsCancel%2A> propriedade do **Cancelar** botão para `true`.  
  
- A tecla ENTER (ou RETURN) como um atalho de teclado que faz com que o **Okey** botão seja pressionado. Você pode fazer isso definindo a <xref:System.Windows.Controls.Button.IsDefault%2A> propriedade do **Okey** botão `true`.  
  
O código a seguir demonstra essa configuração.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
A experiência do usuário em uma caixa de diálogo também se estende à barra de menus da janela que abre a caixa de diálogo. Quando um item de menu executar uma função que exige a interação do usuário por meio de uma caixa de diálogo antes que a função possa continuar, o item de menu da função terá reticências em seu cabeçalho, conforme mostrado aqui.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Quando um item de menu executar uma função que exibe uma caixa de diálogo que não exige a interação do usuário, como uma caixa de diálogo Sobre, as reticências não serão necessárias.  
  
#### <a name="opening-a-modal-dialog-box"></a>Abrindo uma caixa de diálogo modal

Normalmente, uma caixa de diálogo é mostrada como resultado da seleção por um usuário de um item de menu para executar uma função específica ao domínio, como definição das margens de um documento em um processador de texto. A exibição de uma janela como uma caixa de diálogo é semelhante à exibição de uma janela normal, embora ela exija uma configuração adicional específica à caixa de diálogo. O processo completo de criar uma instância, configurar e abrir uma caixa de diálogo é mostrado no código a seguir.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

Aqui, o código passa informações padrão (as margens atuais) para a caixa de diálogo. Ele também define o <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> propriedade com uma referência para a janela que está mostrando a caixa de diálogo. Em geral, você deve sempre definir o proprietário de uma caixa de diálogo para fornecer comportamentos relacionados ao estado de janela que são comuns a todas as caixas de diálogo (consulte [visão geral do Windows WPF](wpf-windows-overview.md) para obter mais informações).

> [!NOTE]
> Você deve fornecer um proprietário para dar suporte à automação de interface do usuário do usuário para caixas de diálogo (consulte [visão geral de automação de interface do usuário](../../ui-automation/ui-automation-overview.md)).

Depois que a caixa de diálogo estiver configurada, ela é mostrada modalmente chamando o <xref:System.Windows.Window.ShowDialog%2A> método.  
  
#### <a name="validating-user-provided-data"></a>Validando dados fornecidos pelo usuário

Quando uma caixa de diálogo é aberta e o usuário fornece os dados necessários, uma caixa de diálogo é responsável por garantir que os dados fornecidos são válidos pelos seguintes motivos:  
  
- De uma perspectiva de segurança, todas as informações devem ser validadas.  
  
- De uma perspectiva específica ao domínio, a validação de dados impede que dados incorretos sejam processados pelo código, o que potencialmente poderá gerar exceções.  
  
- De uma perspectiva da experiência do usuário, uma caixa de diálogo pode ajudar os usuários mostrando-lhes quais dados inseridos são inválidos.  
  
- De uma perspectiva do desempenho, a validação de dados em um aplicativo de várias camadas pode reduzir o número de viagens de ida e volta entre o cliente e as camadas do aplicativo, especialmente, quando o aplicativo é composto por serviços Web ou bancos de dados baseados em servidor.  

Para validar um controle associado no WPF, você precisa definir uma regra de validação e associá-la com a associação. Uma regra de validação é uma classe personalizada que derive de <xref:System.Windows.Controls.ValidationRule>. O exemplo a seguir mostra uma regra de validação `MarginValidationRule`, que verifica se um valor associado é um <xref:System.Double> e está dentro do intervalo especificado.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

Nesse código, a lógica de validação de uma regra de validação é implementada, substituindo o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método, que valida os dados e retorna um apropriado <xref:System.Windows.Controls.ValidationResult>.  

Para associar a regra de validação ao controle associado, use a marcação a seguir.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Depois que a regra de validação estiver associada, WPF aplicará automaticamente quando os dados são inseridos no controle associado. Quando um controle contiver dados inválidos, o WPF exibirá uma borda vermelha ao redor do controle inválido, conforme mostrado na figura a seguir.  
  
![Uma caixa de diálogo margens com uma borda vermelha ao redor do valor da margem esquerda inválida.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF não restringe um usuário ao controle inválido até que ele tenha inserido dados válidos. Esse é bom comportamento para uma caixa de diálogo; um usuário poderá navegar livremente pelos controles em uma caixa de diálogo, independentemente de os dados serem válidos ou não. No entanto, isso significa que um usuário pode inserir dados inválidos e pressionar o **Okey** botão. Por esse motivo, seu código também precisa validar todos os controles em uma caixa de diálogo caixa quando o **Okey** botão for pressionado, tratando o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Esse código enumera todos os objetos de dependência em uma janela e, se houver algum inválidos (conforme retornado por <xref:System.Windows.Controls.Validation.GetHasError%2A>, o controle inválido obterá o foco, o `IsValid` retorno do método `false`, e a janela é considerada inválida.  
  
Depois que uma caixa de diálogo for válida, ela pode ser fechada e retornada com segurança. Como parte do processo de retorno, ela precisa retornar um resultado para a função de chamada.  
  
#### <a name="setting-the-modal-dialog-result"></a>Definindo o resultado da caixa de diálogo modal

Abrindo uma caixa de diálogo usando <xref:System.Windows.Window.ShowDialog%2A> é fundamentalmente como chamar um método: o código que abriu a caixa de diálogo usando <xref:System.Windows.Window.ShowDialog%2A> aguardará até <xref:System.Windows.Window.ShowDialog%2A> retorna. Quando <xref:System.Windows.Window.ShowDialog%2A> retorna, o código que a chamou precisa decidir se continuará ou interromperá o processamento, com base em se o usuário pressionou a **Okey** botão ou o **Cancelar** botão. Para facilitar essa decisão, a caixa de diálogo precisa retornar a escolha do usuário como uma <xref:System.Boolean> valor retornado do <xref:System.Windows.Window.ShowDialog%2A> método.  

Quando o **Okey** botão é clicado, <xref:System.Windows.Window.ShowDialog%2A> deverá retornar `true`. Isso é feito definindo a <xref:System.Windows.Window.DialogResult%2A> caixa de propriedade da caixa de diálogo quando o **Okey** botão é clicado.  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Observe que a configuração de <xref:System.Windows.Window.DialogResult%2A> propriedade também faz com que a janela seja fechada automaticamente, o que minimiza a necessidade de chamar explicitamente <xref:System.Windows.Window.Close%2A>.  
  
Quando o **Cancelar** botão é clicado, <xref:System.Windows.Window.ShowDialog%2A> deverá retornar `false`, que também exige a configuração de <xref:System.Windows.Window.DialogResult%2A> propriedade.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Quando um botão <xref:System.Windows.Controls.Button.IsCancel%2A> estiver definida como `true` e o usuário pressiona o a **Cancelar** botão ou a tecla ESC, <xref:System.Windows.Window.DialogResult%2A> é definido automaticamente como `false`. A marcação a seguir tem o mesmo efeito que o código anterior, sem a necessidade de lidar com o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Uma caixa de diálogo retorna automaticamente `false` quando um usuário pressiona o **fechar** botão na barra de título ou escolhe o **fechar** item de menu a **sistema** menu.  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Processamento de dados retornados de uma caixa de diálogo modal  

Quando <xref:System.Windows.Window.DialogResult%2A> é definido por uma caixa de diálogo, a função que a abriu pode obter o resultado da caixa de diálogo inspecionando a <xref:System.Windows.Window.DialogResult%2A> propriedade quando <xref:System.Windows.Window.ShowDialog%2A> retorna.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Se o resultado da caixa de diálogo for `true`, a função usa como uma indicação para recuperar e processar os dados fornecidos pelo usuário.  
  
> [!NOTE]
> Depois de <xref:System.Windows.Window.ShowDialog%2A> foi retornado, uma caixa de diálogo não pode ser reaberta. Em vez disso, você precisa criar uma nova instância.

Se o resultado da caixa de diálogo for `false`, a função deverá encerrar o processamento de forma adequada.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Criando uma caixa de diálogo personalizada sem janela restrita

Uma caixa de diálogo sem janela restrita, como a Caixa de Diálogo Localizar mostrada na figura a seguir, tem a mesma aparência básica que a caixa de diálogo modal.  

![Captura de tela que mostra uma caixa de diálogo Localizar.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

No entanto, o comportamento é ligeiramente diferente, conforme descrito nas próximas seções.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Abrindo uma caixa de diálogo sem janela restrita

Uma caixa de diálogo sem janela restrita é aberta chamando o <xref:System.Windows.Window.Show%2A> método.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  
 
[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Diferentemente <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> retorna imediatamente. Consequentemente, a janela de chamada não pode saber quando a caixa de diálogo sem janela restrita é fechada e, portanto, não sabe quando procurar um resultado da caixa de diálogo nem quando obter dados da caixa de diálogo para processamento adicional. Em vez disso, a caixa de diálogo precisa criar uma maneira alternativa de retornar dados para a janela de chamada para o processamento.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Processamento de dados retornados de uma caixa de diálogo sem janela restrita  

Neste exemplo, o `FindDialogBox` pode retornar um ou mais encontrar resultados para a janela principal, dependendo do texto que está sendo procurado sem nenhuma frequência específica. Assim como ocorre com uma caixa de diálogo modal, uma caixa de diálogo sem janela restrita pode retornar resultados usando propriedades. No entanto, a janela que possui a caixa de diálogo precisa saber quando deve verificar essas propriedades. Uma maneira de habilitar essa opção é para que a caixa de diálogo implemente um evento que é acionado sempre que um texto é encontrado. `FindDialogBox` implementa o `TextFoundEvent` para essa finalidade, que primeiro exige um delegado.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Usando o `TextFoundEventHandler` delegado `FindDialogBox` implementa o `TextFoundEvent`.
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

Consequentemente, `Find` pode disparar o evento quando um resultado de pesquisa for encontrado.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

A janela do proprietário precisa então se registrar e tratar esse evento.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Fechando uma caixa de diálogo sem janela restrita

Porque <xref:System.Windows.Window.DialogResult%2A> não precisa ser definida, uma caixa de diálogo sem janela restrita pode ser fechada usando o sistema fornecem mecanismos, incluindo o seguinte:  
  
- Clicar a **fechar** botão na barra de título.  
  
- Pressionar ALT + F4.  
  
- Escolhendo **feche** da **sistema** menu.  
  
Como alternativa, seu código pode chamar <xref:System.Windows.Window.Close%2A> quando o **fechar** botão é clicado.  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Consulte também

- [Visão geral do pop-up](../controls/popup-overview.md)
- [Amostra de caixa de diálogo](https://go.microsoft.com/fwlink/?LinkID=159984)
