---
title: 'Instruções passo a passo: hospedando um controle composto dos Windows Forms no WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 22bfcf63fa42e72b3b971b18b5e68aec1e57c649
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536779"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Instruções passo a passo: hospedando um controle composto dos Windows Forms no WPF
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento substancial em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] código, ele pode ser mais eficiente reutilizar pelo menos parte desse código em seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo em vez de reescrevê-la a partir do zero. O cenário mais comum é quando você tem controles Windows Forms existentes. Em alguns casos, talvez você não tenha nem acesso ao código-fonte desses controles. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Fornece um procedimento simples para hospedar esses controles em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo. Por exemplo, você pode usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para a maioria da sua programação enquanto hospeda seus especializado <xref:System.Windows.Forms.DataGridView> controles.  
  
 Este passo a passo orienta você por meio de um aplicativo que hospeda um controle composto do Windows Forms para realizar a entrada de dados em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo. O controle composto é empacotado em uma DLL. Esse procedimento geral pode ser estendido para aplicativos e controles mais complexos. Este passo a passo foi projetado para ser praticamente idêntico em aparência e funcionalidade ao [instruções passo a passo: hospedando um controle composto do WPF nos Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). A principal diferença é que o cenário de hospedagem é invertido.  
  
 O passo a passo está dividido em duas seções. A primeira seção descreve brevemente a implementação de controle de composição dos Windows Forms. A segunda seção descreve detalhadamente como hospedar um controle de composição em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo, receber eventos do controle e como acessar algumas das propriedades do controle.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Implementação do controle de composição dos Windows Forms.  
  
-   Implementação do aplicativo host do WPF.  
  
 Para obter uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [hospedando um controle composto do Windows Forms no WPF de exemplo](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implementação do controle de composição dos Windows Forms  
 O controle composto do Windows Forms usado neste exemplo é um formulário simples de entrada de dados. Este formulário recebe o nome e o endereço do usuário e, em seguida, usa um evento personalizado para retornar essa informação ao host. A ilustração a seguir mostra o controle renderizado.  
  
 ![Controle de formulários simples do Windows](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")  
Controle de composição dos Windows Forms  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1.  Inicie [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]e abra o **novo projeto** caixa de diálogo.  
  
2.  Na categoria janela, selecione a **biblioteca de controle do Windows Forms** modelo.  
  
3.  Dê um nome ao novo projeto `MyControls`.  
  
4.  Para o local, especifique uma pasta nomeada de forma conveniente de nível superior, como `WpfHostingWindowsFormsControl`. Mais tarde, você colocará o aplicativo host nessa pasta.  
  
5.  Clique em **OK** para criar o projeto. O projeto padrão contém um único controle denominado `UserControl1`.  
  
6.  No Gerenciador de soluções, renomeie `UserControl1` para `MyControl1`.  
  
 Seu projeto deve ter referências às seguintes DLLs de sistema. Se qualquer uma dessas DLLs não estiver incluída por padrão, adicione-as ao projeto.  
  
-   Sistema  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Adicionando controles ao formulário  
 Para adicionar controles ao formulário:  
  
-   Abra `MyControl1` no designer.  
  
 Adicione cinco <xref:System.Windows.Forms.Label> controles e suas respectivas <xref:System.Windows.Forms.TextBox> controles, dimensionados e organizados como na ilustração anterior, no formulário. No exemplo, o <xref:System.Windows.Forms.TextBox> controles são nomeados:  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 Adicione duas <xref:System.Windows.Forms.Button> controles rotulados **Okey** e **Cancelar**. No exemplo, os nomes dos botões são `btnOK` e `btnCancel`, respectivamente.  
  
### <a name="implementing-the-supporting-code"></a>Implementando o código de suporte  
 Abra o formulário no modo de exibição de código. O controle retorna os dados coletados para seu host, gerando personalizado `OnButtonClick` eventos. Os dados estão contidos no objeto de argumento do evento. O código a seguir mostra a declaração do evento e do delegado.  
  
 Adicione o seguinte código para o `MyControl1` classe.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 O `MyControlEventArgs` classe contém as informações a serem retornadas para o host.  
  
 Adicione a seguinte classe ao formulário.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 Quando o usuário clica o **Okey** ou **Cancelar** botão, o <xref:System.Windows.Forms.Control.Click> criar manipuladores de eventos uma `MyControlEventArgs` objeto que contém os dados e gera o `OnButtonClick` eventos. A única diferença entre os dois manipuladores é o argumento do evento `IsOK` propriedade. Essa propriedade permite que o host determine qual botão foi clicado. Ele é definido como `true` para o **Okey** botão, e `false` para o **Cancelar** botão. O código a seguir mostra os dois manipuladores de botão.  
  
 Adicione o seguinte código para o `MyControl1` classe.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Fornecendo um nome forte e compilando o assembly  
 Para este assembly a ser referenciado por um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo, ele deve ter um nome forte. Para criar um nome forte, crie um arquivo de chave com Sn.exe e adicioná-lo ao seu projeto.  
  
1.  Abra um prompt de comando do [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]. Para fazer isso, clique o **inicie** menu e, em seguida, selecione **todos os programas/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Prompt de comando**. Isso inicia uma janela de console com variáveis de ambiente personalizadas.  
  
2.  No prompt de comando, use o `cd` comando para ir para a pasta do projeto.  
  
3.  Gere um arquivo de chave chamado MyControls.snk, executando o comando a seguir.  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  Para incluir o arquivo de chave em seu projeto, clique no nome do projeto no Gerenciador de soluções e, em seguida, clique em **propriedades**. No Designer de projeto, clique o **Signing** guia, selecione o **assinar o assembly** caixa de seleção e, em seguida, navegue até o arquivo de chave.  
  
5.  Compile a solução. O build produzirá uma DLL denominada MyControls.dll.  
  
## <a name="implementing-the-wpf-host-application"></a>Implementação do aplicativo host do WPF  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedar o aplicativo usa o <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle que hospedará `MyControl1`. O aplicativo manipula o `OnButtonClick` evento para receber os dados do controle. Ele também tem uma coleção de botões de opção que permitem que você altere algumas das propriedades do controle do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo. A ilustração a seguir mostra o aplicativo concluído.  
  
 ![Um controle inserido em uma página do WPF](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")  
O aplicativo concluído, mostrando o controle inserido no aplicativo do WPF  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1.  Abra [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]e selecione **novo projeto**.  
  
2.  Na categoria janela, selecione a **aplicativo WPF** modelo.
  
3.  Dê um nome ao novo projeto `WpfHost`.  
  
4.  Para o local, especifique a mesma pasta de nível superior que contém o projeto MyControls.  
  
5.  Clique em **OK** para criar o projeto.  
  
 Você também precisará adicionar referências a DLL que contém `MyControl1` e outros assemblies.  
  
1.  Clique no nome do projeto no Gerenciador de soluções e selecione **adicionar referência**.  
  
2.  Clique o **procurar** guia e, em seguida, navegue até a pasta que contém MyControls. Para este passo a passo, a pasta é a MyControls\bin\Debug.  
  
3.  Selecione MyControls e, em seguida, clique em **Okey**.  
  
4.  Adicione uma referência ao assembly WindowsFormsIntegration, que é chamado WindowsFormsIntegration.dll.  
  
### <a name="implementing-the-basic-layout"></a>Implementando o layout básico  
 O [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do host do aplicativo é implementado no MainWindow. XAML. Esse arquivo contém [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] marcação que define o layout e hospeda o controle Windows Forms. O aplicativo é dividido em três regiões:  
  
-   O **propriedades do controle** painel, que contém uma coleção de botões de opção que você pode usar para modificar diversas propriedades do controle hospedado.  
  
-   O **dados de controle** painel, que contém vários <xref:System.Windows.Controls.TextBlock> elementos que exibem os dados retornados do controle hospedado.  
  
-   O próprio controle hospedado.  
  
 O layout básico é mostrado no seguinte XAML. A marcação que é necessário para hospedar `MyControl1` é omitido neste exemplo, mas será abordado posteriormente.  
  
 Substitua o XAML em MainWindow.xaml pelo seguinte. Se você estiver usando Visual Basic, altere a classe para `x:Class="MainWindow"`.  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 A primeira <xref:System.Windows.Controls.StackPanel> elemento contém vários conjuntos de <xref:System.Windows.Controls.RadioButton> controles que permitem que você modifique diversas propriedades padrão do controle hospedado. Ele é seguido por um <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, quais hosts `MyControl1`. O último <xref:System.Windows.Controls.StackPanel> elemento contém vários <xref:System.Windows.Controls.TextBlock> elementos que exibem os dados retornados pelo controle hospedado. A ordenação dos elementos e o <xref:System.Windows.Controls.DockPanel.Dock%2A> e <xref:System.Windows.FrameworkElement.Height%2A> configurações de atributo incorporam o controle hospedado na janela sem espaços ou distorção.  
  
#### <a name="hosting-the-control"></a>Hospedagem do controle  
 A seguinte versão editada do XAML anterior se concentra nos elementos que são necessários para hospedar `MyControl1`.  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 O `xmlns` atributo de mapeamento do namespace cria uma referência para o `MyControls` namespace que contém o controle hospedado. Esse mapeamento permite que você represente `MyControl1` na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] como `<mcl:MyControl1>`.  
  
 Dois elementos no XAML manipulam a hospedagem:  
  
-   `WindowsFormsHost` representa o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento que permite que você hospede um controle Windows Forms em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.  
  
-   `mcl:MyControl1`, que representa `MyControl1`, é adicionado para o <xref:System.Windows.Forms.Integration.WindowsFormsHost> coleção de filhos do elemento. Como resultado, esse controle Windows Forms é renderizado como parte do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] janela e você pode se comunicar com o controle do aplicativo.  
  
### <a name="implementing-the-code-behind-file"></a>Implementando o arquivo code-behind  
 O arquivo code-behind,. XAML. vb ou MainWindow.xaml.cs, contém o código procedural que implementa a funcionalidade do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discutidos na seção anterior. As tarefas principais são:  
  
-   Anexando um manipulador de eventos `MyControl1`do `OnButtonClick` eventos.  
  
-   Modificar diversas propriedades de `MyControl1`, com base em como a coleção de botões de opção é definida.  
  
-   Exibir os dados coletados pelo controle.  
  
#### <a name="initializing-the-application"></a>Inicializando o aplicativo  
 O código de inicialização está contido em um manipulador de eventos da janela <xref:System.Windows.FrameworkElement.Loaded> eventos e anexa um manipulador de eventos para o controle `OnButtonClick` eventos.  
  
 Em XAML. vb ou MainWindow.xaml.cs, adicione o seguinte código para o `MainWindow` classe.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 Porque o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discutido anteriormente adicionou `MyControl1` para o <xref:System.Windows.Forms.Integration.WindowsFormsHost> coleção de elementos filho do elemento, você pode converter o <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> para obter a referência ao `MyControl1`. Em seguida, você pode usar essa referência para anexar um manipulador de eventos `OnButtonClick`.  
  
 Além de fornecer uma referência ao controle em si, <xref:System.Windows.Forms.Integration.WindowsFormsHost> expõe várias propriedades do controle, que você pode manipular a partir do aplicativo. O código de inicialização atribui esses valores a variáveis globais particulares para uso posterior no aplicativo.  
  
 Para que você pode acessar facilmente os tipos na `MyControls` DLL, adicione o seguinte `Imports` ou `using` instrução na parte superior do arquivo.  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a>Manipulando o evento OnButtonClick  
 `MyControl1` aciona o `OnButtonClick` evento quando o usuário clica em qualquer um dos botões do controle.  
  
 Adicione o seguinte código para o `MainWindow` classe.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 Os dados nas caixas de texto são empacotados no `MyControlEventArgs` objeto. Se o usuário clica o **Okey** botão, o manipulador de eventos extrai os dados e o exibe no painel abaixo `MyControl1`.  
  
#### <a name="modifying-the-controls-properties"></a>Modificando as propriedades do controle  
 O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento expõe várias das propriedades padrão do controle hospedado. Como resultado, você pode alterar a aparência do controle para combinar melhor com o estilo do seu aplicativo. Os conjuntos de botões de opção no painel esquerdo permitem ao usuário modificar várias propriedades de fonte e cor. Cada conjunto de botões tem um manipulador para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento, que detecta seleções de botão de opção do usuário e altera a propriedade correspondente no controle.  
  
 Adicione o seguinte código para o `MainWindow` classe.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Crie e execute o aplicativo. Adicione algum texto no controle de composição dos Windows Forms e, em seguida, clique em **Okey**. O texto é exibido nos rótulos. Clique nos diferentes botões de opção para ver o efeito no controle.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [Passo a passo: hospedando um controle do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
