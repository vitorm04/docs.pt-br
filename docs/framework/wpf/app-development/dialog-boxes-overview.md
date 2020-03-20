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
ms.openlocfilehash: c98d6a45d151d4b683a21e48eaeb5f4a19eaadb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187449"
---
# <a name="dialog-boxes-overview"></a>Visão geral das caixas de diálogo
Os aplicativos autônomos normalmente têm uma janela principal que exibe os principais dados sobre os [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] quais o aplicativo opera e expõe a funcionalidade para processar esses dados através de mecanismos como barras de menu, barras de ferramentas e barras de status. Um aplicativo não trivial também pode exibir janelas adicionais para fazer o seguinte:  
  
- Exibir informações específicas aos usuários.  
  
- Coletar informações de usuários.  
  
- Exibir e coletar informações.  
  
 Esses tipos de janelas são conhecidas como *caixas de diálogo*, e existem dois tipos: modal e modeless.  
  
 Uma caixa de diálogo *modal* é exibida por uma função quando a função precisa de dados adicionais de um usuário para continuar. Como a função depende da caixa de diálogo modal para coletar dados, a caixa de diálogo modal também impede que um usuário ative outras janelas no aplicativo enquanto ele está aberto. Na maioria dos casos, uma caixa de diálogo modal permite que um usuário sinalize quando tiver terminado com a caixa de diálogo modal pressionando um botão **OK** ou **Cancel.** Pressionar o botão **OK** indica que um usuário inseriu dados e quer que a função continue sendo processada com esses dados. Pressionar o botão **Cancelar** indica que um usuário deseja impedir que a função seja executada completamente. Os exemplos de caixas de diálogo modais mais comuns são mostrados para abrir, salvar e imprimir dados.  
  
 Uma caixa de diálogo *modeless,* por outro lado, não impede que um usuário acione outras janelas enquanto estiver aberta. Por exemplo, se um usuário desejar localizar ocorrências de uma palavra específica em um documento, uma janela principal geralmente abrirá uma caixa de diálogo para solicitar a um usuário qual palavra ele está procurando. No entanto, como a localização de uma palavra não impede que um usuário edite o documento, a caixa de diálogo não precisa ser restrita. Uma caixa de diálogo modeless pelo menos fornece um botão **Fechar** para fechar a caixa de diálogo e pode fornecer botões adicionais para executar funções específicas, como um botão **Encontrar o Seguinte** para encontrar a próxima palavra que corresponda aos critérios de encontrar uma pesquisa de palavras.  
  
 O Windows Presentation Foundation (WPF) permite criar vários tipos de caixas de diálogo, incluindo caixas de mensagens, caixas de diálogo comuns e caixas de diálogo personalizadas. Este tópico discute cada um, e a [Amostra da Caixa de Diálogo](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) fornece exemplos correspondentes.  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a>Caixas de mensagens  
 Uma *caixa de mensagens* é uma caixa de diálogo que pode ser usada para exibir informações texuais e permitir que os usuários tomem decisões com botões. A figura a seguir mostra uma caixa de mensagem que exibe informações textuais, faz uma pergunta e fornece ao usuário três botões para responder à pergunta.  
  
 ![Uma caixa de diálogo processador de texto perguntando se você deseja salvar as alterações no documento antes que o aplicativo seja fechado.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Para criar uma caixa de <xref:System.Windows.MessageBox> mensagens, você usa a classe. <xref:System.Windows.MessageBox>permite configurar o texto, o título, o ícone e os botões da caixa de mensagem, usando código como o seguinte.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Para mostrar uma caixa de `static` <xref:System.Windows.MessageBox.Show%2A> mensagens, você chama o método, como demonstrado no código a seguir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Quando o código que mostra uma caixa de mensagem precisa detectar e processar a decisão do usuário (qual botão foi pressionado), o código pode inspecionar o resultado da caixa de mensagem, conforme mostrado no código a seguir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Para obter mais informações sobre <xref:System.Windows.MessageBox>o uso de caixas de mensagens, consulte : [Sample messagebox](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)e [box de diálogo](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).  
  
 Embora <xref:System.Windows.MessageBox> possa oferecer uma experiência simples de <xref:System.Windows.MessageBox> usuário de caixa de diálogo, a vantagem de usar é que é o único tipo de janela que pode ser mostrado por aplicativos que são executados dentro de uma caixa de areia de segurança de confiança parcial (ver [Segurança),](../security-wpf.md)como aplicativos de navegador XAML (XBAPs).  
  
 A maioria das caixas de diálogo exibe e coleta dados mais complexos que o resultado de uma caixa de mensagem, incluindo texto, seleção (caixas de seleção), seleção mutuamente exclusiva (botões de opção) e seleção de lista (caixas de listagem, caixas de combinação, caixas de listagem suspensas). Para estes, o Windows Presentation Foundation (WPF) fornece várias caixas de diálogo comuns e permite que você crie suas próprias caixas de diálogo, embora o uso de ambos esteja limitado a aplicativos em execução com total confiança.  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a>Caixas de diálogo comuns  
 O Windows implementa uma variedade de caixas de diálogo reutilizáveis que são comuns a todos os aplicativos, incluindo caixas de diálogo para abrir arquivos, salvar arquivos e imprimir. Como essas caixas de diálogo são implementadas pelo sistema operacional, elas podem ser compartilhadas entre todos os aplicativos executados no sistema operacional, o que ajuda na consistência da experiência do usuário. Quando os usuários estiverem familiarizados com o uso de uma caixa de diálogo fornecida pelo sistema operacional em um aplicativo, eles não precisarão aprender a usar a caixa de diálogo em outros aplicativos. Como essas caixas de diálogo estão disponíveis para todos os aplicativos e por ajudarem a fornecer uma experiência de usuário consistente, elas são conhecidas como *caixas de diálogo comuns*.  
  
 O Windows Presentation Foundation (WPF) encapsula o arquivo aberto, salva o arquivo e imprime caixas de diálogo comuns e as expõe como classes gerenciadas para você usar em aplicativos autônomos. Este tópico fornece uma visão geral breve de cada uma delas.  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a>Diálogo abrir arquivo  
 A caixa de diálogo Abrir Arquivo, mostrada na figura a seguir, é usada pela funcionalidade de abertura de arquivo para recuperar o nome de um arquivo a ser aberto.  
  
 ![Uma caixa de diálogo Abrir mostrando o local para recuperar o arquivo.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 A caixa de diálogo de <xref:Microsoft.Win32.OpenFileDialog> arquivo aberto comum <xref:Microsoft.Win32> é implementada como classe e está localizada no namespace. O código a seguir mostra como criar, configurar e mostrar uma e como processar o resultado.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Para obter mais informações sobre a <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>caixa de diálogo de arquivo aberto, consulte .  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>pode ser usado para recuperar com segurança nomes de arquivos por aplicativos executados com confiança parcial (ver [Segurança](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a>caixa de diálogo Salvar Arquivo  
 A caixa de diálogo Salvar Arquivo, mostrada na figura a seguir, é usada pela funcionalidade de salvamento de arquivo para recuperar o nome de um arquivo a ser salvo.  
  
 ![Uma caixa de diálogo Salvar como mostrava o local para salvar o arquivo.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 A caixa de diálogo de <xref:Microsoft.Win32.SaveFileDialog> arquivo de salvamento comum <xref:Microsoft.Win32> é implementada como classe e está localizada no namespace. O código a seguir mostra como criar, configurar e mostrar uma e como processar o resultado.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Para obter mais informações sobre a <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>caixa de diálogo salvar arquivos, consulte .  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a>caixa de diálogo Imprimir

A caixa de diálogo Imprimir, mostrada na figura a seguir, é usada pela funcionalidade de impressão para escolher e configurar a impressora na qual um usuário deseja imprimir os dados.  
  
![Captura de tela que mostra uma caixa de diálogo Imprimir.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
A caixa de diálogo de <xref:System.Windows.Controls.PrintDialog> impressão comum é <xref:System.Windows.Controls> implementada como classe e está localizada no namespace. O código a seguir mostra como criar, configurar e mostrar uma.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Para obter mais informações sobre <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>a caixa de diálogo de impressão, consulte . Para discussão detalhada da impressão no WPF, consulte [Visão geral de impressão](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a>Caixas de diálogo personalizadas

Embora as caixas de diálogo comuns sejam úteis e devam ser usadas quando possível, elas não dão suporte aos requisitos de caixas de diálogo específicas ao domínio. Nesses casos, você precisa criar suas próprias caixas de diálogo. Como veremos, uma caixa de diálogo é uma janela com comportamentos especiais. <xref:System.Windows.Window>implementa esses comportamentos e, consequentemente, você usa <xref:System.Windows.Window> para criar caixas de diálogo modais e modeladores personalizadas.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a>Criando uma caixa de diálogo personalizada modal

Este tópico mostra <xref:System.Windows.Window> como usar para criar uma implementação `Margins` típica da caixa de diálogo modal, usando a caixa de diálogo como exemplo (ver [Amostra de caixa de diálogo](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)). A `Margins` caixa de diálogo é mostrada na figura a seguir.  
  
 ![Uma caixa de diálogo Margens com campos para definir margem esquerda, margem superior, margem direita e margem inferior.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Configuração de uma caixa de diálogo modal

A interface do usuário de uma caixa de diálogo típica inclui o seguinte:  
  
- Os vários controles que são necessários para coletar os dados desejados.  
  
- Um botão **OK** que os usuários clicam para fechar a caixa de diálogo, retornar à função e continuar o processamento.  
  
- Um botão **Cancelar** que os usuários clicam para fechar a caixa de diálogo e impedir que a função seja processada.  
  
- Um botão **Fechar** na barra de título.  
  
- Um ícone.  
  
- **Minimizar,** **maximizar**e **restaurar** botões.  
  
- Um **menu do sistema** para minimizar, maximizar, restaurar e fechar a caixa de diálogo.  
  
- Uma posição acima e no centro da janela que abriu a caixa de diálogo.  
  
- A capacidade de ser redimensionada sempre que possível para evitar que a caixa de diálogo seja muito pequena e fornecer ao usuário um tamanho padrão útil. Isso requer que você defina as dimensões padrão e mínima.  
  
- A tecla ESC como um atalho de teclado que faz com que o botão **Cancelar** seja pressionado. Você faz isso <xref:System.Windows.Controls.Button.IsCancel%2A> definindo a propriedade `true`do botão **Cancelar** para .  
  
- A tecla ENTER (ou RETURN) como um atalho de teclado que faz com que o botão **OK** seja pressionado. Você faz isso <xref:System.Windows.Controls.Button.IsDefault%2A> definindo a `true`propriedade do botão **OK** .  
  
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

Aqui, o código passa informações padrão (as margens atuais) para a caixa de diálogo. Ele também <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> define a propriedade com uma referência à janela que está mostrando a caixa de diálogo. Em geral, você deve sempre definir o proprietário para uma caixa de diálogo para fornecer comportamentos relacionados ao estado da janela que são comuns a todas as caixas de diálogo (consulte [Visão geral do Windows do WPF](wpf-windows-overview.md) para obter mais informações).

> [!NOTE]
> Você deve fornecer a um proprietário para oferecer suporte à automação da interface do usuário (UI) para caixas de diálogo (ver [Visão geral de automação de interface de interface](../../ui-automation/ui-automation-overview.md)).

Depois que a caixa de diálogo é configurada, ela é mostrada moderadamente chamando o <xref:System.Windows.Window.ShowDialog%2A> método.  
  
#### <a name="validating-user-provided-data"></a>Validação de dados fornecidos pelo usuário

Quando uma caixa de diálogo é aberta e o usuário fornece os dados necessários, uma caixa de diálogo é responsável por garantir que os dados fornecidos são válidos pelos seguintes motivos:  
  
- De uma perspectiva de segurança, todas as informações devem ser validadas.  
  
- De uma perspectiva específica ao domínio, a validação de dados impede que dados incorretos sejam processados pelo código, o que potencialmente poderá gerar exceções.  
  
- De uma perspectiva da experiência do usuário, uma caixa de diálogo pode ajudar os usuários mostrando-lhes quais dados inseridos são inválidos.  
  
- De uma perspectiva do desempenho, a validação de dados em um aplicativo de várias camadas pode reduzir o número de viagens de ida e volta entre o cliente e as camadas do aplicativo, especialmente, quando o aplicativo é composto por serviços Web ou bancos de dados baseados em servidor.  

Para validar um controle vinculado no WPF, você precisa definir uma regra de validação e associá-la à vinculação. Uma regra de validação é uma <xref:System.Windows.Controls.ValidationRule>classe personalizada que deriva de . O exemplo a seguir `MarginValidationRule`mostra uma regra de validação, que verifica se um valor vinculado é um <xref:System.Double> e está dentro de um intervalo especificado.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

Neste código, a lógica de validação de uma <xref:System.Windows.Controls.ValidationRule.Validate%2A> regra de validação é implementada substituindo o método, que valida os dados e retorna um apropriado. <xref:System.Windows.Controls.ValidationResult>  

Para associar a regra de validação ao controle associado, use a marcação a seguir.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Uma vez que a regra de validação esteja associada, o WPF irá aplicá-la automaticamente quando os dados forem inseridos no controle de destino. Quando um controle contém dados inválidos, o WPF exibirá uma borda vermelha em torno do controle inválido, conforme mostrado na figura a seguir.  
  
![Uma caixa de diálogo Margens com uma borda vermelha em torno do valor de margem esquerda inválido.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

O WPF não restringe um usuário ao controle inválido até que ele tenha inserido dados válidos. Esse é bom comportamento para uma caixa de diálogo; um usuário poderá navegar livremente pelos controles em uma caixa de diálogo, independentemente de os dados serem válidos ou não. No entanto, isso significa que um usuário pode inserir dados inválidos e pressionar o botão **OK.** Por essa razão, seu código também precisa validar todos **OK** os controles em uma <xref:System.Windows.Controls.Primitives.ButtonBase.Click> caixa de diálogo quando o botão OK é pressionado manuseando o evento.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Este código enumera todos os objetos de dependência em uma janela e, se houver, inválido (como retornado por <xref:System.Windows.Controls.Validation.GetHasError%2A>, o controle inválido obtém o foco, o `IsValid` método retorna `false`, e a janela é considerada inválida.  
  
Depois que uma caixa de diálogo for válida, ela pode ser fechada e retornada com segurança. Como parte do processo de retorno, ela precisa retornar um resultado para a função de chamada.  
  
#### <a name="setting-the-modal-dialog-result"></a>Definindo o resultado da caixa de diálogo modal

Abrir uma caixa <xref:System.Windows.Window.ShowDialog%2A> de diálogo usando é fundamentalmente como chamar <xref:System.Windows.Window.ShowDialog%2A> um método: o código que abriu a caixa de diálogo usando espera até <xref:System.Windows.Window.ShowDialog%2A> retornar. Quando <xref:System.Windows.Window.ShowDialog%2A> retorna, o código que o chamou precisa decidir se deve continuar processando ou parando o processamento, com base no botão **OK** ou no botão **Cancelar.** Para facilitar essa decisão, a caixa de diálogo precisa <xref:System.Boolean> retornar a escolha <xref:System.Windows.Window.ShowDialog%2A> do usuário como um valor que é devolvido do método.  

Quando o botão **OK** <xref:System.Windows.Window.ShowDialog%2A> estiver `true`clicado, deve retornar . Isso é conseguido <xref:System.Windows.Window.DialogResult%2A> definindo a propriedade da caixa de diálogo quando o botão **OK** é clicado.  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Observe que <xref:System.Windows.Window.DialogResult%2A> a configuração da propriedade também faz com que a <xref:System.Windows.Window.Close%2A>janela feche automaticamente, o que alivia a necessidade de chamar explicitamente .  
  
Quando o botão **Cancelar** <xref:System.Windows.Window.ShowDialog%2A> for `false`clicado, deve <xref:System.Windows.Window.DialogResult%2A> retornar, o que também requer a configuração da propriedade.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Quando a propriedade <xref:System.Windows.Controls.Button.IsCancel%2A> de um `true` botão é definida e o usuário pressiona <xref:System.Windows.Window.DialogResult%2A> o botão `false` **Cancelar** ou a tecla ESC, é automaticamente definido como . A marcação a seguir tem o mesmo efeito do <xref:System.Windows.Controls.Primitives.ButtonBase.Click> código anterior, sem a necessidade de lidar com o evento.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Uma caixa de `false` diálogo retorna automaticamente quando um usuário **pressiona** o botão Fechar na barra de título ou escolhe o item **'Fechar** menu' no menu **Sistema.**  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Processamento de dados retornados de uma caixa de diálogo modal  

Quando <xref:System.Windows.Window.DialogResult%2A> é definida por uma caixa de diálogo, a função que <xref:System.Windows.Window.DialogResult%2A> a <xref:System.Windows.Window.ShowDialog%2A> abriu pode obter o resultado da caixa de diálogo inspecionando a propriedade quando retornar.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Se o resultado `true`da caixa de diálogo for, a função usa isso como uma sugestão para recuperar e processar os dados fornecidos pelo usuário.  
  
> [!NOTE]
> Depois <xref:System.Windows.Window.ShowDialog%2A> de retornado, uma caixa de diálogo não pode ser reaberta. Em vez disso, você precisa criar uma nova instância.

Se o resultado `false`da caixa de diálogo for, a função deve terminar o processamento adequadamente.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a>Criando uma caixa de diálogo personalizada de modeless

Uma caixa de diálogo sem janela restrita, como a Caixa de Diálogo Localizar mostrada na figura a seguir, tem a mesma aparência básica que a caixa de diálogo modal.  

![Captura de tela que mostra uma caixa de diálogo Encontrar.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

No entanto, o comportamento é ligeiramente diferente, conforme descrito nas próximas seções.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Abrindo uma caixa de diálogo modeless

Uma caixa de diálogo modeless <xref:System.Windows.Window.Show%2A> é aberta chamando o método.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Ao <xref:System.Windows.Window.ShowDialog%2A> <xref:System.Windows.Window.Show%2A> contrário, retorna imediatamente. Consequentemente, a janela de chamada não pode saber quando a caixa de diálogo sem janela restrita é fechada e, portanto, não sabe quando procurar um resultado da caixa de diálogo nem quando obter dados da caixa de diálogo para processamento adicional. Em vez disso, a caixa de diálogo precisa criar uma maneira alternativa de retornar dados para a janela de chamada para o processamento.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Processamento de dados retornados de uma caixa de diálogo modeless  

Neste exemplo, `FindDialogBox` o pode retornar um ou mais resultados de encontrar para a janela principal, dependendo do texto que está sendo pesquisado sem qualquer frequência específica. Assim como ocorre com uma caixa de diálogo modal, uma caixa de diálogo sem janela restrita pode retornar resultados usando propriedades. No entanto, a janela que possui a caixa de diálogo precisa saber quando deve verificar essas propriedades. Uma maneira de habilitar essa opção é para que a caixa de diálogo implemente um evento que é acionado sempre que um texto é encontrado. `FindDialogBox`implementa `TextFoundEvent` o para este fim, que primeiro requer um delegado.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Usando `TextFoundEventHandler` o `FindDialogBox` delegado, `TextFoundEvent`implementa o .
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

Consequentemente, `Find` pode aumentar o evento quando um resultado de pesquisa é encontrado.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

A janela do proprietário precisa então se registrar e tratar esse evento.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Fechando uma caixa de diálogo modeless

Como <xref:System.Windows.Window.DialogResult%2A> não precisa ser definido, uma caixa de diálogo modeless pode ser fechada usando mecanismos de fornecer sistema, incluindo o seguinte:  
  
- Clicando no botão **Fechar** na barra de título.  
  
- Pressionar ALT + F4.  
  
- Escolhendo **Fechar** no menu **do sistema.**  
  
Alternativamente, seu código <xref:System.Windows.Window.Close%2A> pode ligar quando o botão **Fechar** é clicado.  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Confira também

- [Visão geral do pop-up](../controls/popup-overview.md)
- [Amostra de caixa de diálogo](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
