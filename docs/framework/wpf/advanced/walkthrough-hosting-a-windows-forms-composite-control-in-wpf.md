---
title: 'Passo a passo: hospedar um controle composto do Windows Forms no WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: e4c1de17b131ee68c6e6fce0035b703eb5b489a0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991878"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Passo a passo: hospedar um controle composto do Windows Forms no WPF
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] substancial em código, pode ser mais eficiente reutilizar pelo menos um pouco desse código em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seu aplicativo em vez de regravá-lo do zero. O cenário mais comum é quando você tem controles de Windows Forms existentes. Em alguns casos, talvez você não tenha nem acesso ao código-fonte desses controles. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece um procedimento direto para hospedar esses controles em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo. Por exemplo, você pode usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para a maior parte de sua programação enquanto hospeda <xref:System.Windows.Forms.DataGridView> seus controles especializados.  
  
 Este passo a passos percorre um aplicativo que hospeda um controle de composição Windows Forms para executar a entrada de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dados em um aplicativo. O controle composto é empacotado em uma DLL. Esse procedimento geral pode ser estendido para aplicativos e controles mais complexos. Este tutorial foi projetado para ser praticamente idêntico na aparência e na funcionalidade [para o Walkthrough: Hospedando um controle composto do WPF](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)em Windows Forms. A principal diferença é que o cenário de hospedagem é invertido.  
  
 O passo a passo está dividido em duas seções. A primeira seção descreve brevemente a implementação do controle composto Windows Forms. A segunda seção aborda em detalhes como hospedar o controle composto em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo, receber eventos do controle e acessar algumas das propriedades do controle.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
- Implementação do controle de composição dos Windows Forms.  
  
- Implementação do aplicativo host do WPF.  
  
 Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [hospedando um Windows Forms controle composto no WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Pré-requisitos  

É necessário o Visual Studio para concluir este passo a passo.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implementação do controle de composição dos Windows Forms  
 O controle composto Windows Forms usado neste exemplo é um formulário simples de entrada de dados. Este formulário recebe o nome e o endereço do usuário e, em seguida, usa um evento personalizado para retornar essa informação ao host. A ilustração a seguir mostra o controle renderizado.  

 A imagem a seguir mostra um controle composto Windows Forms:  

 ![Captura de tela que mostra um controle de Windows Forms simples.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1. Inicie [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]o e abra a caixa de diálogo **novo projeto** .  
  
2. Na categoria de janela, selecione o modelo de **biblioteca de controle de Windows Forms** .  
  
3. Dê um nome ao novo projeto `MyControls`.  
  
4. Para o local, especifique uma pasta de nível superior que `WpfHostingWindowsFormsControl`seja convenientemente nomeada, como. Mais tarde, você colocará o aplicativo host nessa pasta.  
  
5. Clique em **OK** para criar o projeto. O projeto padrão contém um único controle chamado `UserControl1`.  
  
6. Em Gerenciador de soluções, renomeie `UserControl1` como. `MyControl1`  
  
 Seu projeto deve ter referências às seguintes DLLs de sistema. Se qualquer uma dessas DLLs não estiver incluída por padrão, adicione-as ao projeto.  
  
- Sistema  
  
- System.Data  
  
- System.Drawing  
  
- System.Windows.Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Adicionando controles ao formulário  
 Para adicionar controles ao formulário:  
  
- Abra `MyControl1` no designer.  
  
 Adicione cinco <xref:System.Windows.Forms.Label> controles e seus controles <xref:System.Windows.Forms.TextBox> correspondentes, dimensionados e organizados como estão na ilustração anterior, no formulário. No exemplo, os <xref:System.Windows.Forms.TextBox> controles são nomeados:  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 Adicione dois <xref:System.Windows.Forms.Button> controles rotulados **OK** e **Cancelar**. No exemplo, os nomes dos botões são `btnOK` e `btnCancel`, respectivamente.  
  
### <a name="implementing-the-supporting-code"></a>Implementando o código de suporte  
 Abra o formulário no modo de exibição de código. O controle retorna os dados coletados para seu host, gerando `OnButtonClick` o evento personalizado. Os dados estão contidos no objeto de argumento do evento. O código a seguir mostra a declaração do evento e do delegado.  
  
 Adicione o código a seguir à classe `MyControl1`.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 A `MyControlEventArgs` classe contém as informações a serem retornadas ao host.

 Adicione a seguinte classe ao formulário.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Quando o usuário clica no botão **OK** ou **Cancelar** , os <xref:System.Windows.Forms.Control.Click> manipuladores de eventos criam `MyControlEventArgs` um objeto que contém os dados e gera `OnButtonClick` o evento. A única diferença entre os dois manipuladores é a propriedade do argumento `IsOK` de evento. Essa propriedade permite que o host determine qual botão foi clicado. Ele é definido como `true` para o botão **OK** e `false` para o botão **Cancelar** . O código a seguir mostra os dois manipuladores de botão.

 Adicione o código a seguir à classe `MyControl1`.

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Fornecendo um nome forte e compilando o assembly
 Para que este assembly seja referenciado por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] um aplicativo, ele deve ter um nome forte. Para criar um nome forte, crie um arquivo de chave com o Sn. exe e adicione-o ao seu projeto.

1. Abra um prompt de comando do [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]. Para fazer isso, clique no menu **Iniciar** e, em seguida, selecione **todos os programas/Microsoft Visual Studio 2010/ferramentas do Visual Studio/prompt de comando do Visual Studio**. Isso inicia uma janela de console com variáveis de ambiente personalizadas.

2. No prompt de comando, use o `cd` comando para ir para a pasta do projeto.

3. Gere um arquivo de chave chamado MyControls.snk, executando o comando a seguir.

    ```console
    Sn.exe -k MyControls.snk
    ```

4. Para incluir o arquivo de chave em seu projeto, clique com o botão direito do mouse no nome do projeto em Gerenciador de Soluções e clique em **Propriedades**. No designer de projeto, clique na guia **assinatura** , marque a caixa de seleção **assinar o assembly** e, em seguida, navegue até o arquivo de chave.

5. Compile a solução. O build produzirá uma DLL denominada MyControls.dll.

## <a name="implementing-the-wpf-host-application"></a>Implementação do aplicativo host do WPF
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo host usa o <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle para hospedar `MyControl1`. O aplicativo manipula o `OnButtonClick` evento para receber os dados do controle. Ele também tem uma coleção de botões de opção que permitem que você altere algumas das propriedades do controle do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo. A ilustração a seguir mostra o aplicativo concluído.

A imagem a seguir mostra o aplicativo completo, incluindo o controle inserido no aplicativo WPF:

 ![Captura de tela que mostra um controle inserido em uma página do WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Criando o Projeto
 Para iniciar o projeto:

1. Abra [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]e selecione **novo projeto**.

2. Na categoria da janela, selecione o modelo de **aplicativo do WPF** .

3. Dê um nome ao novo projeto `WpfHost`.

4. Para o local, especifique a mesma pasta de nível superior que contém o projeto MyControls.

5. Clique em **OK** para criar o projeto.

 Você também precisa adicionar referências à dll que contém `MyControl1` e a outros assemblies.

1. Clique com o botão direito do mouse no nome do projeto em Gerenciador de Soluções e selecione **Adicionar referência**.

2. Clique na guia **procurar** e navegue até a pasta que contém MyControls. dll. Para este passo a passo, a pasta é a MyControls\bin\Debug.

3. Selecione MyControls. dll e clique em **OK**.

4. Adicione uma referência ao assembly WindowsFormsIntegration, que é chamado WindowsFormsIntegration.dll.

### <a name="implementing-the-basic-layout"></a>Implementando o layout básico
 O [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplicativo host é implementado em MainWindow. XAML. Esse arquivo contém [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] marcação que define o layout e hospeda o controle de Windows Forms. O aplicativo é dividido em três regiões:

- O painel **Propriedades de controle** , que contém uma coleção de botões de opção que você pode usar para modificar várias propriedades do controle hospedado.

- Os **dados do** painel de controle, que contém <xref:System.Windows.Controls.TextBlock> vários elementos que exibem os dados retornados do controle hospedado.

- O próprio controle hospedado.

 O layout básico é mostrado no seguinte XAML. A marcação necessária para hospedar `MyControl1` é omitida neste exemplo, mas será discutida posteriormente.

 Substitua o XAML em MainWindow.xaml pelo seguinte. Se você estiver usando Visual Basic, altere a classe para `x:Class="MainWindow"`.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 O primeiro <xref:System.Windows.Controls.StackPanel> elemento contém vários conjuntos de <xref:System.Windows.Controls.RadioButton> controles que permitem modificar várias propriedades padrão do controle hospedado. Isso é seguido por um <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, que hospeda `MyControl1`. O elemento <xref:System.Windows.Controls.StackPanel> final contém vários <xref:System.Windows.Controls.TextBlock> elementos que exibem os dados retornados pelo controle hospedado. A ordenação dos elementos e <xref:System.Windows.Controls.DockPanel.Dock%2A> das configurações de atributo e <xref:System.Windows.FrameworkElement.Height%2A> incorpora o controle hospedado na janela sem intervalos ou distorção.

#### <a name="hosting-the-control"></a>Hospedagem do controle
 A seguinte versão editada do XAML anterior se concentra nos elementos que são necessários para hospedar `MyControl1`o.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 O `xmlns` atributo de mapeamento de namespace cria uma referência `MyControls` ao namespace que contém o controle hospedado. Esse mapeamento permite que você `MyControl1` represente [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] no `<mcl:MyControl1>`como.

 Dois elementos no XAML manipulam a hospedagem:

- `WindowsFormsHost`representa o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento que permite hospedar um controle de Windows Forms em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.

- `mcl:MyControl1`, que representa `MyControl1`, é adicionado <xref:System.Windows.Forms.Integration.WindowsFormsHost> à coleção filho do elemento. Como resultado, esse Windows Forms controle é renderizado como parte da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] janela e você pode se comunicar com o controle do aplicativo.

### <a name="implementing-the-code-behind-file"></a>Implementando o arquivo code-behind
 O arquivo code-behind, MainWindow. XAML. vb ou MainWindow.XAML.cs, contém o código de procedimento que implementa a funcionalidade do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] abordado na seção anterior. As tarefas principais são:

- Anexando um manipulador de `MyControl1`eventos `OnButtonClick` a um evento.

- Modificar várias propriedades de `MyControl1`, com base em como a coleção de botões de opção é definida.

- Exibir os dados coletados pelo controle.

#### <a name="initializing-the-application"></a>Inicializando o aplicativo
 O código de inicialização está contido em um manipulador de eventos para o <xref:System.Windows.FrameworkElement.Loaded> evento da janela e anexa um manipulador de eventos ao evento `OnButtonClick` do controle.

 Em MainWindow. XAML. vb ou MainWindow.XAML.cs, adicione o código a seguir à `MainWindow` classe.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 Como os [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discutidos anteriormente `MyControl1` foram adicionados <xref:System.Windows.Forms.Integration.WindowsFormsHost> à <xref:System.Windows.Forms.Integration.WindowsFormsHost> `MyControl1`coleção de elementos filho do elemento, você pode converter o elemento paraobterareferênciaa.<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> Você pode usar essa referência para anexar um manipulador de eventos ao `OnButtonClick`.

 Além de fornecer uma referência ao próprio controle, <xref:System.Windows.Forms.Integration.WindowsFormsHost> o expõe uma série de propriedades do controle, que você pode manipular a partir do aplicativo. O código de inicialização atribui esses valores a variáveis globais particulares para uso posterior no aplicativo.

 Para que você possa acessar facilmente os tipos na `MyControls` dll, adicione a seguinte `Imports` instrução ou `using` à parte superior do arquivo.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>Manipulando o evento OnButtonClick
 `MyControl1`gera o `OnButtonClick` evento quando o usuário clica em um dos botões do controle.

 Adicione o código a seguir à classe `MainWindow`.

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Os dados nas caixas de texto são incluídos `MyControlEventArgs` no objeto. Se o usuário clicar no botão **OK** , o manipulador de eventos extrairá os dados e os exibirá no painel `MyControl1`abaixo.

#### <a name="modifying-the-controls-properties"></a>Modificando as propriedades do controle
 O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento expõe várias das propriedades padrão do controle hospedado. Como resultado, você pode alterar a aparência do controle para combinar melhor com o estilo do seu aplicativo. Os conjuntos de botões de opção no painel esquerdo permitem ao usuário modificar várias propriedades de fonte e cor. Cada conjunto de botões tem um manipulador para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento, que detecta as seleções do botão de opção do usuário e altera a propriedade correspondente no controle.

 Adicione o código a seguir à classe `MainWindow`.

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Crie e execute o aplicativo. Adicione texto no controle de composição Windows Forms e clique em **OK**. O texto é exibido nos rótulos. Clique nos diferentes botões de opção para ver o efeito no controle.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Passo a passo: Hospedando um controle de Windows Forms no WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto do WPF no Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
