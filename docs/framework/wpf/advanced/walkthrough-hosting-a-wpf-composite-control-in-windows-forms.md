---
title: 'Passo a passo: hospedar um controle composto do WPF nos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: a062095885e6c1fc8816a78847968b1c250eabf8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991457"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Passo a passo: hospedar um controle composto do WPF nos Windows Forms
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] substancial em código, pode ser mais eficaz estender seu aplicativo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] existente com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em vez de regravá-lo do zero. Um cenário comum é quando você deseja inserir um ou mais controles implementados com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o em seu aplicativo Windows Forms. Para obter mais informações sobre como personalizar controles WPF, consulte [personalização de controle](../controls/control-customization.md).  
  
 Este passo a passos percorre um aplicativo que hospeda um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle composto para executar a entrada de dados em um aplicativo Windows Forms. O controle composto é empacotado em uma DLL. Esse procedimento geral pode ser estendido para aplicativos e controles mais complexos. Este tutorial foi projetado para ser praticamente idêntico na aparência e na funcionalidade [para o Walkthrough: Hospedagem de um controle composto Windows Forms no](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)WPF. A principal diferença é que o cenário de hospedagem é invertido.  
  
 O passo a passo está dividido em duas seções. A primeira seção descreve brevemente a implementação do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle composto. A segunda seção aborda em detalhes como hospedar o controle composto em um aplicativo Windows Forms, receber eventos do controle e acessar algumas das propriedades do controle.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
- Implementação do controle composto do WPF.  
  
- Implementação do aplicativo host do Windows Forms.  
  
 Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [hospedando um controle composto do WPF no exemplo Windows Forms](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Pré-requisitos  

É necessário o Visual Studio para concluir este passo a passo.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementação do controle composto do WPF  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle composto usado neste exemplo é um formulário simples de entrada de dados que usa o nome e o endereço do usuário. Quando o usuário clica em um dos dois botões para indicar que a tarefa foi concluída, o controle gera um evento personalizado para retornar essa informação ao host. A ilustração a seguir mostra o controle renderizado. 

 A imagem a seguir mostra um controle composto do WPF: 

 ![Captura de tela que mostra um controle simples do WPF.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1. Inicie [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]o e abra a caixa de diálogo **novo projeto** .  
  
2. No Visual C# e na categoria Windows, selecione o modelo de **biblioteca de controle de usuário do WPF** .  
  
3. Dê um nome ao novo projeto `MyControls`.  
  
4. Para o local, especifique uma pasta de nível superior que `WindowsFormsHostingWpfControl`seja convenientemente nomeada, como. Mais tarde, você colocará o aplicativo host nessa pasta.  
  
5. Clique em **OK** para criar o projeto. O projeto padrão contém um único controle chamado `UserControl1`.  
  
6. Em Gerenciador de soluções, renomeie `UserControl1` como. `MyControl1`  
  
 Seu projeto deve ter referências às seguintes DLLs de sistema. Se alguma dessas DLLs não estiver incluída por padrão, adicione-a ao projeto.  
  
- PresentationCore  
  
- PresentationFramework  
  
- Sistema  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>Criando a interface do usuário  
 O [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para o controle composto é implementado com [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. O controle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] composto consiste em cinco <xref:System.Windows.Controls.TextBox> elementos. Cada <xref:System.Windows.Controls.TextBox> elemento tem um elemento <xref:System.Windows.Controls.TextBlock> associado que serve como um rótulo. Há dois <xref:System.Windows.Controls.Button> elementos na parte inferior, **OK** e **Cancelar**. Quando o usuário clica em um dos botões, o controle gera um evento personalizado para retornar as informações para o host.  
  
#### <a name="basic-layout"></a>Layout básico  
 Os vários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos estão contidos em um <xref:System.Windows.Controls.Grid> elemento. Você pode usar <xref:System.Windows.Controls.Grid> para organizar o conteúdo do controle composto quase da mesma maneira que usaria um `Table` elemento em HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]também tem um <xref:System.Windows.Documents.Table> elemento, mas <xref:System.Windows.Controls.Grid> é mais leve e mais adequado para tarefas de layout simples.  
  
 O XAML a seguir mostra o layout básico. Esse XAML define a estrutura geral do controle especificando o número de colunas e linhas no <xref:System.Windows.Controls.Grid> elemento.  
  
 No MyControl1.xaml, substitua o XAML existente pelo XAML a seguir.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Adicionando elementos TextBox e TextBlock à grade  
 Você coloca um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elemento na grade definindo os atributos <xref:System.Windows.Controls.Grid.RowProperty> e <xref:System.Windows.Controls.Grid.ColumnProperty> do elemento com o número de linha e coluna apropriado. Lembre-se de que a numeração de linha e coluna é baseada em zero. Você pode fazer com que um elemento abranja várias colunas definindo <xref:System.Windows.Controls.Grid.ColumnSpanProperty> seu atributo. Para obter mais informações <xref:System.Windows.Controls.Grid> sobre elementos, consulte [criar um elemento de grade](../controls/how-to-create-a-grid-element.md).  
  
 O XAML <xref:System.Windows.Controls.TextBox> a seguir mostra os <xref:System.Windows.Controls.TextBlock> elementos e do controle composto com <xref:System.Windows.Controls.Grid.RowProperty> seus <xref:System.Windows.Controls.Grid.ColumnProperty> atributos e, que são definidos para posicionar os elementos corretamente na grade.  
  
 Em MyControl1. XAML, adicione o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Definindo o estilo dos elementos da interface do usuário  
 Muitos dos elementos no formulário de entrada de dados têm uma aparência semelhante, o que significa que têm configurações idênticas para várias de suas propriedades. Em vez de definir os atributos de cada elemento separadamente, o XAML <xref:System.Windows.Style> anterior usa elementos para definir configurações de propriedade padrão para classes de elementos. Essa abordagem reduz a complexidade do controle e permite que você altere a aparência de vários elementos por meio de um único atributo de estilo.  
  
 Os <xref:System.Windows.Style> elementos estão contidos <xref:System.Windows.Controls.Grid> na Propriedade do <xref:System.Windows.FrameworkElement.Resources%2A> elemento, para que possam ser usados por todos os elementos no controle. Se um estilo for nomeado, você o aplicará a um elemento adicionando um <xref:System.Windows.Style> conjunto de elementos ao nome do estilo. Os estilos que não são nomeados tornam-se o estilo padrão para o elemento. Para obter mais informações [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sobre estilos, consulte [estilização e modelagem](../controls/styling-and-templating.md).  
  
 O XAML a seguir mostra <xref:System.Windows.Style> os elementos para o controle composto. Para ver como os estilos são aplicados aos elementos, consulte o XAML anterior. Por exemplo, o último <xref:System.Windows.Controls.TextBlock> elemento tem o `inlineText` estilo e o último <xref:System.Windows.Controls.TextBox> elemento usa o estilo padrão.  
  
 Em MyControl1. XAML, adicione o XAML a seguir logo após <xref:System.Windows.Controls.Grid> o elemento inicial.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Adicionando os botões OK e Cancelar  
 Os elementos finais no controle composto são os elementos **OK** e **Cancelar** <xref:System.Windows.Controls.Button> , que ocupam as duas primeiras colunas <xref:System.Windows.Controls.Grid>da última linha do. Esses elementos usam um manipulador de eventos comum `ButtonClicked`, e o estilo <xref:System.Windows.Controls.Button> padrão definido no XAML anterior.  
  
 Em MyControl1. XAML, adicione o XAML a seguir após o <xref:System.Windows.Controls.TextBox> último elemento. A [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] parte do controle composto agora está concluída.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementando o arquivo code-behind  
 O arquivo code-behind, MyControl1.xaml.cs, implementa três tarefas essenciais:
  
1. Manipula o evento que ocorre quando o usuário clica em um dos botões.  
  
2. Recupera os dados dos <xref:System.Windows.Controls.TextBox> elementos e os empacota em um objeto de argumento de evento personalizado.  
  
3. Gera o evento `OnButtonClick` personalizado, que notifica o host de que o usuário foi concluído e passa os dados de volta para o host.  
  
 O controle também expõe várias propriedades de fonte e cor que permitem que você altere a aparência. Ao contrário <xref:System.Windows.Forms.Integration.WindowsFormsHost> da classe, que é usada para hospedar um controle de Windows Forms <xref:System.Windows.Forms.Integration.ElementHost> , a classe expõe apenas <xref:System.Windows.Controls.Panel.Background%2A> a propriedade do controle. Para manter a similaridade entre este exemplo de código e o exemplo discutido em [passo a passos: Hospedar um controle composto Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), o controle expõe as propriedades restantes diretamente.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>A estrutura básica do arquivo code-behind  
 O arquivo code-behind consiste em um único namespace, `MyControls`, que conterá duas classes, `MyControl1` e `MyControlEventArgs`.  
  
```csharp  
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
  
 A primeira classe, `MyControl1`, é uma classe parcial que contém o código que implementa a funcionalidade [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do definida em MyControl1. XAML. Quando MyControl1. XAML é analisado, o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é convertido na mesma classe parcial e as duas classes parciais são mescladas para formar o controle compilado. Por esse motivo, o nome de classe no arquivo code-behind deve corresponder ao nome de classe designado para MyControl1.xaml e precisa herdar do elemento raiz do controle. A segunda classe, `MyControlEventArgs`, é uma classe de argumentos de evento que é usada para enviar os dados de volta para o host.  
  
 Abra MyControl1.xaml.cs. Altere a declaração de classe existente para que ela tenha o seguinte nome e herde de <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicializando o controle  
 O código a seguir implementa várias tarefas básicas:  
  
- Declara um evento particular, `OnButtonClick`, e seu delegado associado,. `MyControlEventHandler`  
  
- Cria diversas variáveis globais privadas que armazenam os dados do usuário. Esses dados são expostos por meio de propriedades correspondentes.  
  
- Implementa um manipulador, `Init`, para o evento do <xref:System.Windows.FrameworkElement.Loaded> controle. Esse manipulador inicializa as variáveis globais ao lhes designar os valores definidos no MyControl1.xaml. Para fazer isso, ele usa o <xref:System.Windows.FrameworkElement.Name%2A> atribuído a um elemento <xref:System.Windows.Controls.TextBlock> típico, `nameLabel`, para acessar as configurações de Propriedade do elemento.  
  
 Exclua o Construtor existente e adicione o código a seguir `MyControl1` à sua classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Manipulando os eventos de clique dos botões  
 O usuário indica que a tarefa de entrada de dados foi concluída clicando no botão **OK** ou no botão **Cancelar** . Ambos os botões usam o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> mesmo manipulador de `ButtonClicked`eventos,. Ambos os botões têm um nome `btnOK` ou `btnCancel`, que habilita o manipulador para determinar qual botão foi clicado `sender` examinando o valor do argumento. O manipulador faz o seguinte:  
  
- Cria um `MyControlEventArgs` objeto que contém os dados <xref:System.Windows.Controls.TextBox> dos elementos.  
  
- Se o usuário clicou no botão **Cancelar** , define `MyControlEventArgs` a propriedade `IsOK` do objeto `false`como.  
  
- Gera o `OnButtonClick` evento para indicar ao host que o usuário está concluído e retorna os dados coletados.  
  
 Adicione o código a seguir à `MyControl1` sua classe, após `Init` o método.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Criando propriedades  
 O restante da classe simplesmente expõe propriedades que correspondem às variáveis globais discutidas anteriormente. Quando uma propriedade é alterada, o acessador definido modifica a aparência do controle ao alterar as propriedades de elemento correspondentes e atualizar as variáveis globais subjacentes.  
  
 Adicione o código a seguir à `MyControl1` sua classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Devolvendo os dados ao host  
 O componente final no arquivo é a `MyControlEventArgs` classe, que é usada para enviar os dados coletados de volta para o host.  
  
 Adicione o código a seguir ao `MyControls` seu namespace. A implementação é simples e não é abordada mais à frente.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Compile a solução. O build produzirá uma DLL denominada MyControls.dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Implementação do aplicativo host do Windows Forms  
 O aplicativo host Windows Forms usa um <xref:System.Windows.Forms.Integration.ElementHost> objeto para hospedar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle composto. O aplicativo manipula o `OnButtonClick` evento para receber os dados do controle composto. O aplicativo também tem um conjunto de botões de opção que podem ser usados para modificar a aparência do controle. A ilustração a seguir mostra o aplicativo.  

A imagem a seguir mostra um controle composto WPF hospedado em um aplicativo Windows Forms "  

 ![Scteenshot que mostra um controle Avalon de Hospedagem de formulários do Windows.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1. Inicie [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]o e abra a caixa de diálogo **novo projeto** .  
  
2. No Visual C# e na categoria Windows, selecione o modelo de **aplicativo Windows Forms** .  
  
3. Dê um nome ao novo projeto `WFHost`.  
  
4. Para o local, especifique a mesma pasta de nível superior que contém o projeto MyControls.  
  
5. Clique em **OK** para criar o projeto.  
  
 Você também precisa adicionar referências à dll que contém `MyControl1` e a outros assemblies.  
  
1. Clique com o botão direito do mouse no nome do projeto em Gerenciador de Soluções e selecione **Adicionar referência**.  
  
2. Clique na guia **procurar** e navegue até a pasta que contém MyControls. dll. Para este passo a passo, a pasta é a MyControls\bin\Debug.  
  
3. Selecione MyControls. dll e clique em **OK**.  
  
4. Adicione referências aos assemblies a seguir.  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - System.Xaml  
  
    - WindowsBase  
  
    - WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementando a interface do usuário para o aplicativo  
 A interface do usuário para o aplicativo do Windows Forms contém vários controles para interagir com o controle composto do WPF.  
  
1. Abra o Form1 no Designer de Formulários do Windows.  
  
2. Amplie o formulário para acomodar os controles.  
  
3. No canto superior direito do formulário, adicione um <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> controle para manter o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle composto.  
  
4. Adicione os seguintes <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> controles ao formulário.  
  
    |Nome|Texto|  
    |----------|----------|  
    |groupBox1|Cor do Plano de Fundo|  
    |groupBox2|Cor do Primeiro Plano|  
    |groupBox3|Tamanho da fonte|  
    |groupBox4|Família de Fontes|  
    |groupBox5|Estilo de fonte|  
    |groupBox6|Espessura da fonte|  
    |groupBox7|Dados de controle|  
  
5. Adicione os controles <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> a seguir <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> aos controles.  
  
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
  
6. Adicione os seguintes <xref:System.Windows.Forms.Label?displayProperty=nameWithType> controles ao último. <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> Esses controles exibem os dados retornados pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle composto.  
  
    |GroupBox|Nome|Texto|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nome:|  
    |groupBox7|lblAddress|Endereço:|  
    |groupBox7|lblCity|Cidade:|  
    |groupBox7|lblState|Estado:|  
    |groupBox7|lblZip|CEP:|  
  
### <a name="initializing-the-form"></a>Inicializando o formulário  
 Geralmente, você implementa o código de hospedagem no manipulador <xref:System.Windows.Forms.Form.Load> de eventos do formulário. O código a seguir mostra <xref:System.Windows.Forms.Form.Load> o manipulador de eventos, um manipulador [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para o evento <xref:System.Windows.FrameworkElement.Loaded> do controle composto e declarações para várias variáveis globais que são usadas posteriormente.  
  
 No designer de formulários do Windows, clique duas vezes no formulário para criar um <xref:System.Windows.Forms.Form.Load> manipulador de eventos. Na parte superior de Form1.cs, adicione as instruções `using` a seguir.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Substitua o conteúdo da classe existente `Form1` pelo código a seguir.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 O `Form1_Load` método no código anterior mostra o procedimento geral para hospedar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle:  
  
1. Crie um novo <xref:System.Windows.Forms.Integration.ElementHost> objeto.  
  
2. Defina a propriedade do <xref:System.Windows.Forms.Control.Dock%2A> controle como <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3. Adicione o <xref:System.Windows.Forms.Integration.ElementHost> controle <xref:System.Windows.Forms.Panel> à coleção do <xref:System.Windows.Forms.Control.Controls%2A> controle.  
  
4. Crie uma instância do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle.  
  
5. Hospede o controle composto no formulário atribuindo o controle à <xref:System.Windows.Forms.Integration.ElementHost> Propriedade do <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> controle.  
  
 As duas linhas restantes no `Form1_Load` método anexam manipuladores a dois eventos de controle:  
  
- `OnButtonClick`é um evento personalizado que é acionado pelo controle composto quando o usuário clica no botão **OK** ou **Cancelar** . O evento é manipulado para obter a resposta do usuário e coletar os dados especificados por ele.  
  
- <xref:System.Windows.FrameworkElement.Loaded>é um evento padrão que é gerado por um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle quando ele é totalmente carregado. O evento é usado aqui porque o exemplo precisa inicializar diversas variáveis globais usando propriedades do controle. No momento do evento do <xref:System.Windows.Forms.Form.Load> formulário, o controle não está totalmente carregado e esses valores ainda estão definidos como. `null` Você precisa aguardar até que o evento <xref:System.Windows.FrameworkElement.Loaded> do controle ocorra antes de poder acessar essas propriedades.  
  
 O <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos é mostrado no código anterior. O `OnButtonClick` manipulador é abordado na próxima seção.  
  
### <a name="handling-onbuttonclick"></a>Manipulando o OnButtonClick  
 O `OnButtonClick` evento ocorre quando o usuário clica no botão **OK** ou **Cancelar** .  
  
 O manipulador de eventos verifica o campo do `IsOK` argumento de evento para determinar qual botão foi clicado. As `lbl` *variáveis de dados* correspondem aos controlesqueforamdiscutidosanteriormente.<xref:System.Windows.Forms.Label> Se o usuário clicar no botão **OK** , os dados dos <xref:System.Windows.Controls.TextBox> controles do controle serão atribuídos ao controle correspondente. <xref:System.Windows.Forms.Label> Se o usuário clicar em **Cancelar**, <xref:System.Windows.Forms.Label.Text%2A> os valores serão definidos como as cadeias de caracteres padrão.  
  
 Adicione o código de manipulador de eventos de clique ao `Form1` botão a seguir à classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Crie e execute o aplicativo. Adicione texto no controle composto do WPF e clique em **OK**. O texto é exibido nos rótulos. Neste ponto, não foi adicionado um código para manipular os botões de opção.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modificando a aparência do controle  
 Os <xref:System.Windows.Forms.RadioButton> controles do formulário permitirão que o usuário altere as [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cores de primeiro e segundo plano do controle composto, bem como várias propriedades de fonte. A cor do plano de fundo é <xref:System.Windows.Forms.Integration.ElementHost> exposta pelo objeto. As propriedades restantes são expostas como propriedades personalizadas do controle.  
  
 Clique duas vezes em <xref:System.Windows.Forms.RadioButton> cada controle no formulário para criar <xref:System.Windows.Forms.RadioButton.CheckedChanged> manipuladores de eventos. Substitua os <xref:System.Windows.Forms.RadioButton.CheckedChanged> manipuladores de eventos pelo código a seguir.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Crie e execute o aplicativo. Clique nos diferentes botões de opção para ver o efeito no controle composto do WPF.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Passo a passo: Hospedando um controle composto Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto do WPF 3D no Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
