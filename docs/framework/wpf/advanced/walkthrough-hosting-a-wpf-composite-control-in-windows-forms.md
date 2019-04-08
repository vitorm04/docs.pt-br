---
title: 'Passo a passo: Hospedando um controle composto do WPF nos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: d38a9c67edb5df89554e9e02274410a825b3384b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654543"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Passo a passo: Hospedando um controle composto do WPF nos Windows Forms
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento substancial em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] código, pode ser mais eficiente estender seu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplicativo com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em vez de reescrevê-la a partir do zero. Um cenário comum é quando você deseja inserir um ou mais controles implementados com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro de seu aplicativo de formulários do Windows. Para obter mais informações sobre como personalizar controles do WPF, consulte [personalização do controle](../controls/control-customization.md).  
  
 Este passo a passo orienta você por meio de um aplicativo que hospeda um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle composto para realizar a entrada de dados em um aplicativo Windows Forms. O controle composto é empacotado em uma DLL. Esse procedimento geral pode ser estendido para aplicativos e controles mais complexos. Este passo a passo foi projetado para ser praticamente idêntico em aparência e funcionalidade ao [passo a passo: Hospedar um Windows Forms de controle de composição no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). A principal diferença é que o cenário de hospedagem é invertido.  
  
 O passo a passo está dividido em duas seções. A primeira seção descreve brevemente a implementação do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle de composição. A segunda seção descreve detalhadamente como hospedar o controle de composição em um aplicativo Windows Forms, receber eventos do controle e acessar algumas das propriedades do controle.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Implementação do controle composto do WPF.  
  
-   Implementação do aplicativo host do Windows Forms.  
  
 Para obter uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [hospedando um controle composto do WPF no Windows Forms exemplo](https://go.microsoft.com/fwlink/?LinkID=159996).  
  
## <a name="prerequisites"></a>Pré-requisitos  

É necessário o Visual Studio para concluir este passo a passo.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementação do controle composto do WPF  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle de composição usado neste exemplo é um formulário de entrada de dados simples que usa o nome e o endereço do usuário. Quando o usuário clica em um dos dois botões para indicar que a tarefa foi concluída, o controle gera um evento personalizado para retornar essa informação ao host. A ilustração a seguir mostra o controle renderizado. 

 A imagem a seguir mostra um controle composto do WPF: 

  
 ![Captura de tela que mostra um controle simples do WPF.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1.  Inicie [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]e abra o **novo projeto** caixa de diálogo.  
  
2.  No Visual C# e a categoria do Windows, selecione o **biblioteca de controle de usuário do WPF** modelo.  
  
3.  Dê um nome ao novo projeto `MyControls`.  
  
4.  Para o local, especifique uma pasta nomeada de forma conveniente de nível superior, como `WindowsFormsHostingWpfControl`. Mais tarde, você colocará o aplicativo host nessa pasta.  
  
5.  Clique em **OK** para criar o projeto. O projeto padrão contém um único controle denominado `UserControl1`.  
  
6.  No Gerenciador de soluções, renomeie `UserControl1` para `MyControl1`.  
  
 Seu projeto deve ter referências às seguintes DLLs de sistema. Se alguma dessas DLLs não estiver incluída por padrão, adicione-a ao projeto.  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   Sistema  
  
-   WindowsBase  
  
### <a name="creating-the-user-interface"></a>Criando a interface do usuário  
 O [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para o controle composto é implementado com [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. O controle de composição [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] consiste em cinco <xref:System.Windows.Controls.TextBox> elementos. Cada <xref:System.Windows.Controls.TextBox> elemento deve possuir um <xref:System.Windows.Controls.TextBlock> elemento que serve como um rótulo. Há dois <xref:System.Windows.Controls.Button> elementos na parte inferior **Okey** e **Cancelar**. Quando o usuário clica em um dos botões, o controle gera um evento personalizado para retornar as informações para o host.  
  
#### <a name="basic-layout"></a>Layout básico  
 As várias [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos estão contidos em um <xref:System.Windows.Controls.Grid> elemento. Você pode usar <xref:System.Windows.Controls.Grid> para organizar o conteúdo da composição de controle quase a mesma maneira como você usaria um `Table` elemento em HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também tem um <xref:System.Windows.Documents.Table> elemento, mas <xref:System.Windows.Controls.Grid> é mais leve e mais adequado para tarefas simples de layout.  
  
 O XAML a seguir mostra o layout básico. Esse XAML define a estrutura geral do controle especificando o número de colunas e as linhas as <xref:System.Windows.Controls.Grid> elemento.  
  
 No MyControl1.xaml, substitua o XAML existente pelo XAML a seguir.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Adicionando elementos TextBox e TextBlock à grade  
 Você coloca um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elemento na grade, definindo o elemento <xref:System.Windows.Controls.Grid.RowProperty> e <xref:System.Windows.Controls.Grid.ColumnProperty> atributos para o número de linha e coluna apropriado. Lembre-se de que a numeração de linha e coluna é baseada em zero. Você pode ter um elemento abranger várias colunas, definindo seu <xref:System.Windows.Controls.Grid.ColumnSpanProperty> atributo. Para obter mais informações sobre <xref:System.Windows.Controls.Grid> elementos, consulte [criar um elemento de grade](../controls/how-to-create-a-grid-element.md).  
  
 O XAML a seguir mostra o controle de composição <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.TextBlock> elementos com seus <xref:System.Windows.Controls.Grid.RowProperty> e <xref:System.Windows.Controls.Grid.ColumnProperty> atributos, que são definidos para colocar os elementos corretamente na grade.  
  
 No MyControl1.xaml, adicione o seguinte XAML dentro do <xref:System.Windows.Controls.Grid> elemento.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Definindo o estilo dos elementos da interface do usuário  
 Muitos dos elementos no formulário de entrada de dados têm uma aparência semelhante, o que significa que têm configurações idênticas para várias de suas propriedades. Em vez de definir atributos de cada elemento separadamente, o XAML anterior utiliza <xref:System.Windows.Style> elementos para definir configurações de propriedade padrão para classes de elementos. Essa abordagem reduz a complexidade do controle e permite que você altere a aparência de vários elementos por meio de um único atributo de estilo.  
  
 O <xref:System.Windows.Style> elementos estão contidos na <xref:System.Windows.Controls.Grid> do elemento <xref:System.Windows.FrameworkElement.Resources%2A> propriedade, para que possam ser usados por todos os elementos no controle. Se um estilo for nomeado, você aplicá-la a um elemento com a adição de um <xref:System.Windows.Style> elemento definido como o nome do estilo. Os estilos que não são nomeados tornam-se o estilo padrão para o elemento. Para obter mais informações sobre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] estilos, consulte [Styling and Templating](../controls/styling-and-templating.md).  
  
 O XAML a seguir mostra o <xref:System.Windows.Style> elementos para o controle composto. Para ver como os estilos são aplicados aos elementos, consulte o XAML anterior. Por exemplo, a última <xref:System.Windows.Controls.TextBlock> elemento tem o `inlineText` estilo e o último <xref:System.Windows.Controls.TextBox> elemento usa o estilo padrão.  
  
 No MyControl1.xaml, adicione o XAML a seguir logo após o <xref:System.Windows.Controls.Grid> se elemento inicial.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Adicionando os botões OK e Cancelar  
 Os últimos elementos do controle composto são os **Okey** e **Cancelar** <xref:System.Windows.Controls.Button> elementos, que ocupam as duas primeiras colunas da última linha do <xref:System.Windows.Controls.Grid>. Esses elementos usam um manipulador de eventos comuns `ButtonClicked`e o padrão <xref:System.Windows.Controls.Button> estilo definido no XAML anterior.  
  
 No MyControl1.xaml, adicione o seguinte XAML após a última <xref:System.Windows.Controls.TextBox> elemento. O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] parte do controle de composição agora está concluída.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementando o arquivo code-behind  
 O arquivo code-behind, MyControl1.xaml.cs, implementa três tarefas essenciais:
  
1.  Manipula o evento que ocorre quando o usuário clica em um dos botões.  
  
2.  Recupera os dados a partir de <xref:System.Windows.Controls.TextBox> elementos e os empacota em um objeto de argumento de evento personalizado.  
  
3.  Aciona o personalizado `OnButtonClick` evento, que notifica o host que o usuário terminou e passa os dados de volta para o host.  
  
 O controle também expõe várias propriedades de fonte e cor que permitem que você altere a aparência. Ao contrário do <xref:System.Windows.Forms.Integration.WindowsFormsHost> classe, que é usado para hospedar um controle dos Windows Forms, o <xref:System.Windows.Forms.Integration.ElementHost> classe expõe o controle <xref:System.Windows.Controls.Panel.Background%2A> apenas com a propriedade. Para manter a semelhança entre esse exemplo de código e o exemplo discutido no [passo a passo: Hospedando um controle composto do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), o controle expõe as propriedades restantes diretamente.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>A estrutura básica do arquivo code-behind  
 O arquivo code-behind consiste em um único namespace, `MyControls`, que contém duas classes, `MyControl1` e `MyControlEventArgs`.  
  
```  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
```  
  
 A primeira classe, `MyControl1`, é uma classe parcial que contém o código que implementa a funcionalidade do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definidos no MyControl1.xaml. Quando o MyControl1.xaml é analisado, o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é convertido para a mesma classe parcial, e as duas classes parciais são mescladas para formar o controle compilado. Por esse motivo, o nome de classe no arquivo code-behind deve corresponder ao nome de classe designado para MyControl1.xaml e precisa herdar do elemento raiz do controle. A segunda classe, `MyControlEventArgs`, é uma classe de argumentos de evento que é usada para enviar os dados de volta para o host.  
  
 Abra MyControl1.xaml.cs. Altere a declaração de classe existente para que ele tem o seguinte nome e herda de <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicializando o controle  
 O código a seguir implementa várias tarefas básicas:  
  
-   Declara um evento privado, `OnButtonClick`e seu delegado associado, `MyControlEventHandler`.  
  
-   Cria diversas variáveis globais privadas que armazenam os dados do usuário. Esses dados são expostos por meio de propriedades correspondentes.  
  
-   Implementa um manipulador `Init`, para o controle <xref:System.Windows.FrameworkElement.Loaded> eventos. Esse manipulador inicializa as variáveis globais ao lhes designar os valores definidos no MyControl1.xaml. Para fazer isso, ele usa o <xref:System.Windows.FrameworkElement.Name%2A> atribuído a um típico <xref:System.Windows.Controls.TextBlock> elemento, `nameLabel`, para acessar as configurações de propriedade desse elemento.  
  
 Exclua o construtor existente e adicione o seguinte código ao seu `MyControl1` classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Manipulando os eventos de clique dos botões  
 O usuário indica que a tarefa de entrada de dados é concluída, clicando em qualquer um de **Okey** botão ou o **Cancelar** botão. Ambos os botões usam o mesmo <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos, `ButtonClicked`. Ambos os botões têm um nome, `btnOK` ou `btnCancel`, que permite que o manipulador determine qual botão foi clicado examinando o valor da `sender` argumento. O manipulador faz o seguinte:  
  
-   Cria uma `MyControlEventArgs` objeto que contém os dados a partir de <xref:System.Windows.Controls.TextBox> elementos.  
  
-   Se o usuário clicou o **Cancelar** botão conjuntos a `MyControlEventArgs` do objeto `IsOK` propriedade `false`.  
  
-   Aciona o `OnButtonClick` evento para indicar ao host que o usuário for concluído e devolve os dados coletados.  
  
 Adicione o seguinte código ao seu `MyControl1` classe, após o `Init` método.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Criando propriedades  
 O restante da classe simplesmente expõe propriedades que correspondem às variáveis globais discutidas anteriormente. Quando uma propriedade é alterada, o acessador definido modifica a aparência do controle ao alterar as propriedades de elemento correspondentes e atualizar as variáveis globais subjacentes.  
  
 Adicione o seguinte código ao seu `MyControl1` classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Devolvendo os dados ao host  
 O componente final no arquivo é o `MyControlEventArgs` classe, que é usado para enviar os dados coletados no host.  
  
 Adicione o seguinte código ao seu `MyControls` namespace. A implementação é simples e não é abordada mais à frente.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Compile a solução. O build produzirá uma DLL denominada MyControls.dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Implementação do aplicativo host do Windows Forms  
 Os formulários do Windows hospedar o aplicativo usa um <xref:System.Windows.Forms.Integration.ElementHost> objeto para hospedar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle de composição. O aplicativo manipula o `OnButtonClick` evento para receber os dados do controle de composição. O aplicativo também tem um conjunto de botões de opção que podem ser usados para modificar a aparência do controle. A ilustração a seguir mostra o aplicativo.  

A imagem a seguir mostra um controle composto do WPF hospedado em um aplicativo de formulários do Windows"  

 ![Scteenshot que mostra um controle Avalon de hospedagem de formulário do Windows.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1.  Inicie [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]e abra o **novo projeto** caixa de diálogo.  
  
2.  No Visual C# e a categoria do Windows, selecione o **aplicativo do Windows Forms** modelo.  
  
3.  Dê um nome ao novo projeto `WFHost`.  
  
4.  Para o local, especifique a mesma pasta de nível superior que contém o projeto MyControls.  
  
5.  Clique em **OK** para criar o projeto.  
  
 Você também precisará adicionar referências a DLL que contém `MyControl1` e outros assemblies.  
  
1.  O nome do projeto no Gerenciador de soluções e selecione **adicionar referência**.  
  
2.  Clique o **procurar** guia e, em seguida, navegue até a pasta que contém MyControls. Para este passo a passo, a pasta é a MyControls\bin\Debug.  
  
3.  Selecione MyControls e, em seguida, clique em **Okey**.  
  
4.  Adicione referências aos assemblies a seguir.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementando a interface do usuário para o aplicativo  
 A interface do usuário para o aplicativo do Windows Forms contém vários controles para interagir com o controle composto do WPF.  
  
1.  Abra o Form1 no Designer de Formulários do Windows.  
  
2.  Amplie o formulário para acomodar os controles.  
  
3.  No canto superior direito do formulário, adicione uma <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> controle para manter o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle de composição.  
  
4.  Adicione o seguinte <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> controles ao formulário.  
  
    |Nome|Texto|  
    |----------|----------|  
    |groupBox1|Cor do Plano de Fundo|  
    |groupBox2|Cor do Primeiro Plano|  
    |groupBox3|Tamanho da fonte|  
    |groupBox4|Família de Fontes|  
    |groupBox5|Estilo de fonte|  
    |groupBox6|Espessura da fonte|  
    |groupBox7|Dados de controle|  
  
5.  Adicione o seguinte <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> controles para o <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> controles.  
  
    |GroupBox|Nome|Texto|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Original|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|Original|  
    |groupBox2|radioForegroundRed|Vermelho|  
    |groupBox2|radioForegroundYellow|Amarelo|  
    |groupBox3|radioSizeOriginal|Original|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Original|  
    |groupBox4|radioFamilyTimes|Times New Roman|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normal|  
    |groupBox5|radioStyleItalic|Italic|  
    |groupBox6|radioWeightOriginal|Original|  
    |groupBox6|radioWeightBold|Em negrito|  
  
6.  Adicione o seguinte <xref:System.Windows.Forms.Label?displayProperty=nameWithType> controla ao último <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Esses controles exibem os dados retornados pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle de composição.  
  
    |GroupBox|Nome|Texto|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nome:|  
    |groupBox7|lblAddress|Endereço:|  
    |groupBox7|lblCity|Cidade:|  
    |groupBox7|lblState|Estado:|  
    |groupBox7|lblZip|CEP:|  
  
### <a name="initializing-the-form"></a>Inicializando o formulário  
 Você geralmente implementa o código de hospedagem do formulário <xref:System.Windows.Forms.Form.Load> manipulador de eventos. O código a seguir mostra a <xref:System.Windows.Forms.Form.Load> manipulador de eventos, um manipulador para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do controle composto <xref:System.Windows.FrameworkElement.Loaded> eventos e declarações para diversas variáveis globais que são usadas mais tarde.  
  
 No Designer de formulários do Windows, clique duas vezes no formulário para criar um <xref:System.Windows.Forms.Form.Load> manipulador de eventos. Na parte superior de Form1.cs, adicione o seguinte `using` instruções.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Substitua o conteúdo do existente `Form1` classe pelo código a seguir.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 O `Form1_Load` método no código anterior mostra o procedimento geral para hospedar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle:  
  
1.  Criar um novo <xref:System.Windows.Forms.Integration.ElementHost> objeto.  
  
2.  Defina o controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3.  Adicione a <xref:System.Windows.Forms.Integration.ElementHost> o controle para o <xref:System.Windows.Forms.Panel> do controle <xref:System.Windows.Forms.Control.Controls%2A> coleção.  
  
4.  Criar uma instância da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle.  
  
5.  Hospedar o controle composto no formulário, atribuindo o controle para o <xref:System.Windows.Forms.Integration.ElementHost> do controle <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> propriedade.  
  
 As duas linhas restantes no `Form1_Load` método anexar manipuladores a dois eventos de controle:  
  
-   `OnButtonClick` é um evento personalizado que é acionado pelo controle de composição quando o usuário clica o **Okey** ou **Cancelar** botão. O evento é manipulado para obter a resposta do usuário e coletar os dados especificados por ele.  
  
-   <xref:System.Windows.FrameworkElement.Loaded> é um evento padrão que é gerado por um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle quando ele está totalmente carregado. O evento é usado aqui porque o exemplo precisa inicializar diversas variáveis globais usando propriedades do controle. No momento do formulário <xref:System.Windows.Forms.Form.Load> evento, o controle não está totalmente carregado e os valores ainda são definidos como `null`. Você precisa esperar até que o controle <xref:System.Windows.FrameworkElement.Loaded> evento ocorre antes de poder acessar essas propriedades.  
  
 O <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos é mostrado no código anterior. O `OnButtonClick` manipulador é abordado na próxima seção.  
  
### <a name="handling-onbuttonclick"></a>Manipulando o OnButtonClick  
 O `OnButtonClick` evento ocorre quando o usuário clica o **Okey** ou **Cancelar** botão.  
  
 O manipulador de eventos verifica o argumento do evento `IsOK` campo para determinar qual botão foi clicado. O `lbl` *dados* variáveis correspondem do <xref:System.Windows.Forms.Label> controles que foram abordados anteriormente. Se o usuário clica o **Okey** botão, os dados a partir do controle <xref:System.Windows.Controls.TextBox> controles é atribuído para os respectivos <xref:System.Windows.Forms.Label> controle. Se o usuário clica **cancele**, o <xref:System.Windows.Forms.Label.Text%2A> valores são definidos como as cadeias de caracteres padrão.  
  
 Adicione o seguinte botão clique em código de manipulador de eventos para o `Form1` classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Crie e execute o aplicativo. Adicione algum texto no controle composto do WPF e, em seguida, clique em **Okey**. O texto é exibido nos rótulos. Neste ponto, não foi adicionado um código para manipular os botões de opção.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modificando a aparência do controle  
 O <xref:System.Windows.Forms.RadioButton> controles no formulário permitirá que o usuário altere a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , bem como várias propriedades de fonte de cores de primeiro plano e o plano de fundo do controle composto. A cor de plano de fundo é exposta pelo <xref:System.Windows.Forms.Integration.ElementHost> objeto. As propriedades restantes são expostas como propriedades personalizadas do controle.  
  
 Clique duas vezes em cada <xref:System.Windows.Forms.RadioButton> controle no formulário para criar <xref:System.Windows.Forms.RadioButton.CheckedChanged> manipuladores de eventos. Substitua o <xref:System.Windows.Forms.RadioButton.CheckedChanged> manipuladores de eventos com o código a seguir.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Crie e execute o aplicativo. Clique nos diferentes botões de opção para ver o efeito no controle composto do WPF.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Passo a passo: Hospedando um controle composto do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto do WPF 3D nos Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
