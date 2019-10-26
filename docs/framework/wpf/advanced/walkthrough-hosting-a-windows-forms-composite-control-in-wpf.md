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
ms.openlocfilehash: e30b1bb45cc2dae2783cddf54dda400b742cdf73
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920325"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Instruções passo a passo: hospedando um controle composto dos Windows Forms no WPF
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente sofisticado para criação de aplicativos. No entanto, quando você tem um investimento substancial em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] código, pode ser mais eficiente reutilizar pelo menos um pouco esse código em seu aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em vez de regravá-lo do zero. O cenário mais comum é quando você tem controles de Windows Forms existentes. Em alguns casos, talvez você não tenha nem acesso ao código-fonte desses controles. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece um procedimento direto para hospedar esses controles em um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Por exemplo, você pode usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para a maior parte de sua programação enquanto hospeda seus controles de <xref:System.Windows.Forms.DataGridView> especializados.  
  
 Este passo a passos percorre um aplicativo que hospeda um controle de composição Windows Forms para executar a entrada de dados em um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O controle composto é empacotado em uma DLL. Esse procedimento geral pode ser estendido para aplicativos e controles mais complexos. Este tutorial foi projetado para ser praticamente idêntico em aparência e funcionalidade para [passo a passos: hospedar um controle composto do WPF em Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). A principal diferença é que o cenário de hospedagem é invertido.  
  
 O passo a passo está dividido em duas seções. A primeira seção descreve brevemente a implementação do controle composto Windows Forms. A segunda seção aborda em detalhes como hospedar o controle composto em um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], receber eventos do controle e acessar algumas das propriedades do controle.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
- Implementação do controle de composição dos Windows Forms.  
  
- Implementação do aplicativo host do WPF.  
  
 Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [hospedando um Windows Forms controle composto no WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Prerequisites  

É necessário o Visual Studio para concluir este passo a passo.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implementação do controle de composição dos Windows Forms  
 O controle composto Windows Forms usado neste exemplo é um formulário simples de entrada de dados. Este formulário recebe o nome e o endereço do usuário e, em seguida, usa um evento personalizado para retornar essa informação ao host. A ilustração a seguir mostra o controle renderizado.  

 A imagem a seguir mostra um controle composto Windows Forms:  

 ![Captura de tela que mostra um controle de Windows Forms simples.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1. Inicie o Visual Studio e abra a caixa de diálogo **novo projeto** .  
  
2. Na categoria de janela, selecione o modelo de **biblioteca de controle de Windows Forms** .  
  
3. Dê um nome ao novo projeto `MyControls`.  
  
4. Para o local, especifique uma pasta de nível superior que seja convenientemente nomeada, como `WpfHostingWindowsFormsControl`. Mais tarde, você colocará o aplicativo host nessa pasta.  
  
5. Clique em **OK** para criar o projeto. O projeto padrão contém um único controle chamado `UserControl1`.  
  
6. Em Gerenciador de Soluções, renomeie `UserControl1` como `MyControl1`.  
  
 Seu projeto deve ter referências às seguintes DLLs de sistema. Se qualquer uma dessas DLLs não estiver incluída por padrão, adicione-as ao projeto.  
  
- Sistema  
  
- System.Data  
  
- System.Drawing  
  
- System.Windows.Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Adicionando controles ao formulário  
 Para adicionar controles ao formulário:  
  
- Abra `MyControl1` no designer.  
  
 Adicione cinco controles de <xref:System.Windows.Forms.Label> e seus controles de <xref:System.Windows.Forms.TextBox> correspondentes, dimensionados e organizados como estão na ilustração anterior, no formulário. No exemplo, os controles de <xref:System.Windows.Forms.TextBox> são nomeados:  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 Adicione dois controles de <xref:System.Windows.Forms.Button> rotulados como **OK** e **Cancelar**. No exemplo, os nomes dos botões são `btnOK` e `btnCancel`, respectivamente.  
  
### <a name="implementing-the-supporting-code"></a>Implementando o código de suporte  
 Abra o formulário no modo de exibição de código. O controle retorna os dados coletados para seu host, gerando o evento de `OnButtonClick` personalizado. Os dados estão contidos no objeto de argumento do evento. O código a seguir mostra a declaração do evento e do delegado.  
  
 Adicione o código a seguir à classe `MyControl1`.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 A classe `MyControlEventArgs` contém as informações a serem retornadas para o host.

 Adicione a seguinte classe ao formulário.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Quando o usuário clica no botão **OK** ou **Cancelar** , os manipuladores de eventos de <xref:System.Windows.Forms.Control.Click> criam um objeto `MyControlEventArgs` que contém os dados e gera o evento `OnButtonClick`. A única diferença entre os dois manipuladores é a propriedade de `IsOK` do argumento de evento. Essa propriedade permite que o host determine qual botão foi clicado. Ele é definido como `true` para o botão **OK** e `false` para o botão **Cancelar** . O código a seguir mostra os dois manipuladores de botão.

 Adicione o código a seguir à classe `MyControl1`.

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Fornecendo um nome forte e compilando o assembly
 Para que este assembly seja referenciado por um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ele deve ter um nome forte. Para criar um nome forte, crie um arquivo de chave com o Sn. exe e adicione-o ao seu projeto.

1. Abra um prompt de comando do Visual Studio. Para fazer isso, clique no menu **Iniciar** e, em seguida, selecione **todos os programas/Microsoft Visual Studio 2010/ferramentas do Visual Studio/prompt de comando do Visual Studio**. Isso inicia uma janela de console com variáveis de ambiente personalizadas.

2. No prompt de comando, use o comando `cd` para ir para a pasta do projeto.

3. Gere um arquivo de chave chamado MyControls.snk, executando o comando a seguir.

    ```console
    Sn.exe -k MyControls.snk
    ```

4. Para incluir o arquivo de chave em seu projeto, clique com o botão direito do mouse no nome do projeto em Gerenciador de Soluções e clique em **Propriedades**. No designer de projeto, clique na guia **assinatura** , marque a caixa de seleção **assinar o assembly** e, em seguida, navegue até o arquivo de chave.

5. Compile a solução. O build produzirá uma DLL denominada MyControls.dll.

## <a name="implementing-the-wpf-host-application"></a>Implementação do aplicativo host do WPF
 O aplicativo host [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa o controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> para hospedar `MyControl1`. O aplicativo manipula o evento `OnButtonClick` para receber os dados do controle. Ele também tem uma coleção de botões de opção que permitem alterar algumas das propriedades do controle do aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A ilustração a seguir mostra o aplicativo concluído.

A imagem a seguir mostra o aplicativo completo, incluindo o controle inserido no aplicativo WPF:

 ![Captura de tela que mostra um controle inserido em uma página do WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Criando o Projeto
 Para iniciar o projeto:

1. Abra o Visual Studio e selecione **novo projeto**.

2. Na categoria da janela, selecione o modelo de **aplicativo do WPF** .

3. Dê um nome ao novo projeto `WpfHost`.

4. Para o local, especifique a mesma pasta de nível superior que contém o projeto MyControls.

5. Clique em **OK** para criar o projeto.

 Você também precisa adicionar referências à DLL que contém `MyControl1` e outros assemblies.

1. Clique com o botão direito do mouse no nome do projeto em Gerenciador de Soluções e selecione **Adicionar referência**.

2. Clique na guia **procurar** e navegue até a pasta que contém MyControls. dll. Para este passo a passo, a pasta é a MyControls\bin\Debug.

3. Selecione MyControls. dll e clique em **OK**.

4. Adicione uma referência ao assembly WindowsFormsIntegration, que é chamado WindowsFormsIntegration.dll.

### <a name="implementing-the-basic-layout"></a>Implementando o layout básico
 A [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplicativo host é implementada em MainWindow. XAML. Esse arquivo contém [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] marcação que define o layout e hospeda o controle de Windows Forms. O aplicativo é dividido em três regiões:

- O painel **Propriedades de controle** , que contém uma coleção de botões de opção que você pode usar para modificar várias propriedades do controle hospedado.

- Os **dados do** painel de controle, que contém vários elementos <xref:System.Windows.Controls.TextBlock> que exibem os dados retornados do controle hospedado.

- O próprio controle hospedado.

 O layout básico é mostrado no seguinte XAML. A marcação necessária para hospedar `MyControl1` é omitida neste exemplo, mas será discutida posteriormente.

 Substitua o XAML em MainWindow.xaml pelo seguinte. Se você estiver usando Visual Basic, altere a classe para `x:Class="MainWindow"`.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 O primeiro elemento <xref:System.Windows.Controls.StackPanel> contém vários conjuntos de controles <xref:System.Windows.Controls.RadioButton> que permitem modificar várias propriedades padrão do controle hospedado. Isso é seguido por um elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>, que hospeda `MyControl1`. O elemento <xref:System.Windows.Controls.StackPanel> final contém vários elementos <xref:System.Windows.Controls.TextBlock> que exibem os dados retornados pelo controle hospedado. A ordenação dos elementos e as configurações de atributo <xref:System.Windows.Controls.DockPanel.Dock%2A> e <xref:System.Windows.FrameworkElement.Height%2A> incorporam o controle hospedado na janela sem intervalos ou distorção.

#### <a name="hosting-the-control"></a>Hospedagem do controle
 A seguinte versão editada do XAML anterior se concentra nos elementos que são necessários para hospedar `MyControl1`.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 O atributo de mapeamento de namespace `xmlns` cria uma referência ao namespace `MyControls` que contém o controle hospedado. Esse mapeamento permite que você represente `MyControl1` no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] como `<mcl:MyControl1>`.

 Dois elementos no XAML manipulam a hospedagem:

- `WindowsFormsHost` representa o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> que permite hospedar um controle de Windows Forms em um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

- `mcl:MyControl1`, que representa `MyControl1`, é adicionado à coleção filho do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Como resultado, esse Windows Forms controle é renderizado como parte da janela [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], e você pode se comunicar com o controle do aplicativo.

### <a name="implementing-the-code-behind-file"></a>Implementando o arquivo code-behind
 O arquivo code-behind, MainWindow. XAML. vb ou MainWindow.xaml.cs, contém o código de procedimento que implementa a funcionalidade do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discutido na seção anterior. As tarefas principais são:

- Anexando um manipulador de eventos ao evento de `OnButtonClick` `MyControl1`.

- Modificar várias propriedades de `MyControl1`, com base em como a coleção de botões de opção é definida.

- Exibir os dados coletados pelo controle.

#### <a name="initializing-the-application"></a>Inicializando o aplicativo
 O código de inicialização está contido em um manipulador de eventos para o evento de <xref:System.Windows.FrameworkElement.Loaded> da janela e anexa um manipulador de eventos ao evento de `OnButtonClick` do controle.

 Em MainWindow. XAML. vb ou MainWindow.xaml.cs, adicione o código a seguir à classe `MainWindow`.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 Como a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discutida anteriormente `MyControl1` à coleção de elementos filho do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>, você pode converter a <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> para obter a referência a `MyControl1`. Em seguida, você pode usar essa referência para anexar um manipulador de eventos a `OnButtonClick`.

 Além de fornecer uma referência ao próprio controle, <xref:System.Windows.Forms.Integration.WindowsFormsHost> expõe um número de propriedades do controle, que você pode manipular a partir do aplicativo. O código de inicialização atribui esses valores a variáveis globais particulares para uso posterior no aplicativo.

 Para que você possa acessar facilmente os tipos na DLL `MyControls`, adicione a seguinte `Imports` ou `using` instrução à parte superior do arquivo.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>Manipulando o evento OnButtonClick
 `MyControl1` gera o evento `OnButtonClick` quando o usuário clica em um dos botões do controle.

 Adicione o código a seguir à classe `MainWindow`.

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Os dados nas caixas de texto são incluídos no objeto `MyControlEventArgs`. Se o usuário clicar no botão **OK** , o manipulador de eventos extrairá os dados e os exibirá no painel abaixo `MyControl1`.

#### <a name="modifying-the-controls-properties"></a>Modificando as propriedades do controle
 O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> expõe várias das propriedades padrão do controle hospedado. Como resultado, você pode alterar a aparência do controle para combinar melhor com o estilo do seu aplicativo. Os conjuntos de botões de opção no painel esquerdo permitem ao usuário modificar várias propriedades de fonte e cor. Cada conjunto de botões tem um manipulador para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, que detecta as seleções do botão de opção do usuário e altera a propriedade correspondente no controle.

 Adicione o código a seguir à classe `MainWindow`.

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Crie e execute o aplicativo. Adicione texto no controle de composição Windows Forms e clique em **OK**. O texto é exibido nos rótulos. Clique nos diferentes botões de opção para ver o efeito no controle.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Passo a passo: hospedando um controle do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Passo a passo: hospedando um controle composto do WPF no Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
