---
title: Hospede um controle composto WPF em Formulários windows
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: e3326f654e05ef7d487a76f076f8ad0da3637096
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187240"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Instruções passo a passo: hospedando um controle composto do WPF nos Windows Forms
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento substancial no código do Windows Forms, pode ser mais eficaz estender o aplicativo Windows Forms existente com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em vez de reescrevê-lo do zero. Um cenário comum é quando você deseja incorporar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] um ou mais controles implementados dentro do aplicativo Windows Forms. Para obter mais informações sobre a personalização dos controles WPF, consulte [Personalização de controle](../controls/control-customization.md).  
  
 Este passo a passo passa por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] um aplicativo que hospeda um controle composto para executar a entrada de dados em um aplicativo do Windows Forms. O controle composto é empacotado em uma DLL. Esse procedimento geral pode ser estendido para aplicativos e controles mais complexos. Este passo a passo foi projetado para ser quase idêntico em aparência e funcionalidade ao Passo a [Passo: Hospedando um Controle Composto de Formulários do Windows no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). A principal diferença é que o cenário de hospedagem é invertido.  
  
 O passo a passo está dividido em duas seções. A primeira seção descreve brevemente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a implementação do controle composto. A segunda seção discute detalhadamente como hospedar o controle composto em um aplicativo do Windows Forms, receber eventos do controle e acessar algumas das propriedades do controle.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
- Implementação do controle composto do WPF.  
  
- Implementação do aplicativo host do Windows Forms.  
  
 Para obter uma lista completa de código das tarefas ilustradas neste passo a passo, consulte [Hospedando um Controle Composto WPF na Amostra de Formulários do Windows](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Pré-requisitos  

É necessário o Visual Studio para concluir este passo a passo.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementação do controle composto do WPF  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle composto usado neste exemplo é um formulário simples de entrada de dados que leva o nome e endereço do usuário. Quando o usuário clica em um dos dois botões para indicar que a tarefa foi concluída, o controle gera um evento personalizado para retornar essa informação ao host. A ilustração a seguir mostra o controle renderizado.

 A imagem a seguir mostra um controle composto WPF:

 ![Captura de tela que mostra um simples controle WPF.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1. Inicie o Visual Studio e abra a caixa de diálogo **do Novo Projeto.**  
  
2. No Visual C# e na categoria Windows, selecione o modelo **Biblioteca de Controle de Usuário do WPF.**  
  
3. Dê um nome ao novo projeto `MyControls`.  
  
4. Para a localização, especifique uma pasta `WindowsFormsHostingWpfControl`de nível superior convenientemente nomeada, como . Mais tarde, você colocará o aplicativo host nessa pasta.  
  
5. Clique em **OK** para criar o projeto. O projeto padrão contém `UserControl1`um único controle chamado .  
  
6. No Solution Explorer, `UserControl1` `MyControl1`renomeie para .  
  
 Seu projeto deve ter referências às seguintes DLLs de sistema. Se alguma dessas DLLs não estiver incluída por padrão, adicione-a ao projeto.  
  
- PresentationCore  
  
- PresentationFramework  
  
- Sistema  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>Criando a interface do usuário  
 O [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] controle composto é [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]implementado com . O controle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] composto consiste <xref:System.Windows.Controls.TextBox> em cinco elementos. Cada <xref:System.Windows.Controls.TextBox> elemento tem <xref:System.Windows.Controls.TextBlock> um elemento associado que serve como rótulo. Há dois <xref:System.Windows.Controls.Button> elementos na parte inferior, **OK** e **Cancel**. Quando o usuário clica em um dos botões, o controle gera um evento personalizado para retornar as informações para o host.  
  
#### <a name="basic-layout"></a>Layout básico  
 Os [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vários elementos <xref:System.Windows.Controls.Grid> estão contidos em um elemento. Você pode <xref:System.Windows.Controls.Grid> usar para organizar o conteúdo do controle composto `Table` da mesma forma que você usaria um elemento em HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]também tem <xref:System.Windows.Documents.Table> um <xref:System.Windows.Controls.Grid> elemento, mas é mais leve e mais adequado para tarefas simples de layout.  
  
 O XAML a seguir mostra o layout básico. Este XAML define a estrutura geral do controle especificando o número <xref:System.Windows.Controls.Grid> de colunas e linhas no elemento.  
  
 No MyControl1.xaml, substitua o XAML existente pelo XAML a seguir.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Adicionando elementos TextBox e TextBlock à grade  
 Você coloca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] um elemento na grade definindo o elemento <xref:System.Windows.Controls.Grid.RowProperty> e <xref:System.Windows.Controls.Grid.ColumnProperty> os atributos para a linha e o número da coluna apropriados. Lembre-se de que a numeração de linha e coluna é baseada em zero. Você pode ter um elemento abrangendo <xref:System.Windows.Controls.Grid.ColumnSpanProperty> várias colunas definindo seu atributo. Para obter <xref:System.Windows.Controls.Grid> mais informações sobre elementos, consulte [Criar um Elemento de Grade](../controls/how-to-create-a-grid-element.md).  
  
 O XAML a seguir mostra <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBlock> o controle <xref:System.Windows.Controls.Grid.RowProperty> <xref:System.Windows.Controls.Grid.ColumnProperty> composto e os elementos com seus atributos, que são definidos para colocar os elementos corretamente na grade.  
  
 Em MyControl1.xaml, adicione o Seguinte <xref:System.Windows.Controls.Grid> XAML dentro do elemento.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Definindo o estilo dos elementos da interface do usuário  
 Muitos dos elementos no formulário de entrada de dados têm uma aparência semelhante, o que significa que têm configurações idênticas para várias de suas propriedades. Em vez de definir os atributos de cada <xref:System.Windows.Style> elemento separadamente, o XAML anterior usa elementos para definir configurações de propriedade padrão para classes de elementos. Essa abordagem reduz a complexidade do controle e permite que você altere a aparência de vários elementos por meio de um único atributo de estilo.  
  
 Os <xref:System.Windows.Style> elementos estão <xref:System.Windows.Controls.Grid> contidos <xref:System.Windows.FrameworkElement.Resources%2A> na propriedade do elemento, para que possam ser usados por todos os elementos do controle. Se um estilo for nomeado, você o <xref:System.Windows.Style> aplica a um elemento adicionando um elemento definido ao nome do estilo. Os estilos que não são nomeados tornam-se o estilo padrão para o elemento. Para obter [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mais informações sobre estilos, consulte [Styling e Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 O XAML a <xref:System.Windows.Style> seguir mostra os elementos para o controle composto. Para ver como os estilos são aplicados aos elementos, consulte o XAML anterior. Por exemplo, <xref:System.Windows.Controls.TextBlock> o último `inlineText` elemento tem <xref:System.Windows.Controls.TextBox> o estilo, e o último elemento usa o estilo padrão.  
  
 Em MyControl1.xaml, adicione o seguinte XAML logo após o <xref:System.Windows.Controls.Grid> elemento inicial.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Adicionando os botões OK e Cancelar  
 Os elementos finais no controle composto são os elementos **OK** e **Cancel,** <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Grid>que ocupam as duas primeiras colunas da última linha do . Esses elementos usam um `ButtonClicked`manipulador de <xref:System.Windows.Controls.Button> eventos comum, e o estilo padrão definido no XAML anterior.  
  
 Em MyControl1.xaml, adicione o seguinte XAML após o último <xref:System.Windows.Controls.TextBox> elemento. A [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] parte do controle composto está agora completa.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementando o arquivo code-behind  
 O arquivo de código traseiro, MyControl1.xaml.cs, implementa três tarefas essenciais:
  
1. Manipula o evento que ocorre quando o usuário clica em um dos botões.  
  
2. Recupera os dados <xref:System.Windows.Controls.TextBox> dos elementos e os empacota em um objeto de argumento de evento personalizado.  
  
3. Levanta o `OnButtonClick` evento personalizado, que notifica o host de que o usuário está acabado e repassa os dados para o host.  
  
 O controle também expõe várias propriedades de fonte e cor que permitem que você altere a aparência. Ao <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrário da classe, que é usada <xref:System.Windows.Forms.Integration.ElementHost> para hospedar um controle <xref:System.Windows.Controls.Panel.Background%2A> do Windows Forms, a classe expõe apenas a propriedade do controle. Para manter a semelhança entre este exemplo de código e o exemplo discutido no [Passo a Passo: Hospedar um Controle Composto de Formulários do Windows no WPF,](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)o controle expõe diretamente as propriedades restantes.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>A estrutura básica do arquivo code-behind  
 O arquivo de código atrás consiste em `MyControls`um único namespace, `MyControlEventArgs`que conterá duas classes e `MyControl1` .  
  
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
  
 A primeira `MyControl1`classe, é uma classe parcial contendo o código [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que implementa a funcionalidade do definido em MyControl1.xaml. Quando o MyControl1.xaml é [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] analisado, o é convertido para a mesma classe parcial, e as duas classes parciais são mescladas para formar o controle compilado. Por esse motivo, o nome de classe no arquivo code-behind deve corresponder ao nome de classe designado para MyControl1.xaml e precisa herdar do elemento raiz do controle. A segunda `MyControlEventArgs`classe, é uma classe de argumentos de evento que é usada para enviar os dados de volta para o host.  
  
 Abra MyControl1.xaml.cs. Alterar a declaração de classe existente para que ela <xref:System.Windows.Controls.Grid>tenha o seguinte nome e herde de .  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicializando o controle  
 O código a seguir implementa várias tarefas básicas:  
  
- Declara um evento `OnButtonClick`privado, e seu `MyControlEventHandler`delegado associado, .  
  
- Cria diversas variáveis globais privadas que armazenam os dados do usuário. Esses dados são expostos por meio de propriedades correspondentes.  
  
- Implementa um `Init`manipulador, para o <xref:System.Windows.FrameworkElement.Loaded> evento do controle. Esse manipulador inicializa as variáveis globais ao lhes designar os valores definidos no MyControl1.xaml. Para fazer isso, <xref:System.Windows.FrameworkElement.Name%2A> ele usa o <xref:System.Windows.Controls.TextBlock> atribuído `nameLabel`a um elemento típico, para acessar as configurações de propriedade desse elemento.  
  
 Exclua o construtor existente e adicione `MyControl1` o seguinte código à sua classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Manipulando os eventos de clique dos botões  
 O usuário indica que a tarefa de entrada de dados está concluída clicando no botão **OK** ou no botão **Cancelar.** Ambos os botões <xref:System.Windows.Controls.Primitives.ButtonBase.Click> usam o `ButtonClicked`mesmo manipulador de eventos, . Ambos os botões têm `btnOK` `btnCancel`um nome, ou , que permite ao manipulador determinar `sender` qual botão foi clicado examinando o valor do argumento. O manipulador faz o seguinte:  
  
- Cria `MyControlEventArgs` um objeto que contém <xref:System.Windows.Controls.TextBox> os dados dos elementos.  
  
- Se o usuário clicou no `MyControlEventArgs` botão **Cancelar,** definirá a propriedade do `IsOK` objeto como `false`.  
  
- Eleva `OnButtonClick` o evento para indicar ao host que o usuário está acabado e repassa os dados coletados.  
  
 Adicione o seguinte `MyControl1` código à `Init` sua classe, após o método.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Criando propriedades  
 O restante da classe simplesmente expõe propriedades que correspondem às variáveis globais discutidas anteriormente. Quando uma propriedade é alterada, o acessador definido modifica a aparência do controle ao alterar as propriedades de elemento correspondentes e atualizar as variáveis globais subjacentes.  
  
 Adicione o seguinte `MyControl1` código à sua classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Devolvendo os dados ao host  
 O componente final do `MyControlEventArgs` arquivo é a classe, que é usada para enviar os dados coletados de volta para o host.  
  
 Adicione o seguinte `MyControls` código ao seu namespace. A implementação é simples e não é abordada mais à frente.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Compile a solução. O build produzirá uma DLL denominada MyControls.dll.  
  
<a name="winforms_host_section"></a>
## <a name="implementing-the-windows-forms-host-application"></a>Implementação do aplicativo host do Windows Forms  
 O aplicativo host Do <xref:System.Windows.Forms.Integration.ElementHost> Windows Forms [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa um objeto para hospedar o controle composto. O aplicativo lida `OnButtonClick` com o evento para receber os dados do controle composto. O aplicativo também tem um conjunto de botões de opção que podem ser usados para modificar a aparência do controle. A ilustração a seguir mostra o aplicativo.  

A imagem a seguir mostra um controle composto WPF hospedado em um aplicativo Do Windows Forms"  

 ![Scteenshot que mostra um controle Avalon de hospedagem do Formulário do Windows.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Criando o Projeto  
 Para iniciar o projeto:  
  
1. Inicie o Visual Studio e abra a caixa de diálogo **do Novo Projeto.**  
  
2. No Visual C# e na categoria Windows, selecione o modelo **de aplicativo de formulários do Windows.**  
  
3. Dê um nome ao novo projeto `WFHost`.  
  
4. Para o local, especifique a mesma pasta de nível superior que contém o projeto MyControls.  
  
5. Clique em **OK** para criar o projeto.  
  
 Você também precisa adicionar referências à `MyControl1` DLL que contém e outras assembléias.  
  
1. Clique com o botão direito do mouse no nome do projeto no Solution Explorer e selecione **Adicionar referência**.  
  
2. Clique na guia **Procurar** e navegue até a pasta que contém MyControls.dll. Para este passo a passo, a pasta é a MyControls\bin\Debug.  
  
3. Selecione MyControls.dll e clique em **OK**.  
  
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
  
3. No canto superior direito do formulário, adicione <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] um controle para manter o controle composto.  
  
4. Adicione os <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> seguintes controles ao formulário.  
  
    |Nome|Texto|  
    |----------|----------|  
    |groupBox1|Cor da tela de fundo|  
    |groupBox2|Cor do Primeiro Plano|  
    |groupBox3|Tamanho da fonte|  
    |groupBox4|Família de Fontes|  
    |groupBox5|Estilo de fonte|  
    |groupBox6|Espessura da fonte|  
    |groupBox7|Dados de controle|  
  
5. Adicione os <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> seguintes <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> controles aos controles.  
  
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
    |groupBox6|radioWeightBold|Negrito|  
  
6. Adicione os <xref:System.Windows.Forms.Label?displayProperty=nameWithType> seguintes controles <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>ao último . Esses controles exibem os dados [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] retornados pelo controle composto.  
  
    |GroupBox|Nome|Texto|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nome:|  
    |groupBox7|lblAddress|Endereço:|  
    |groupBox7|lblCity|Cidade:|  
    |groupBox7|lblState|Estado:|  
    |groupBox7|lblZip|CEP:|  
  
### <a name="initializing-the-form"></a>Inicializando o formulário  
 Você geralmente implementa o código de <xref:System.Windows.Forms.Form.Load> hospedagem no manipulador de eventos do formulário. O código a <xref:System.Windows.Forms.Form.Load> seguir mostra o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] manipulador de <xref:System.Windows.FrameworkElement.Loaded> eventos, um manipulador para o evento do controle composto e declarações para várias variáveis globais que são usadas mais tarde.  
  
 No Windows Forms Designer, clique duas vezes <xref:System.Windows.Forms.Form.Load> no formulário para criar um manipulador de eventos. No topo do Form1.cs, `using` adicione as seguintes declarações.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Substitua o conteúdo `Form1` da classe existente pelo seguinte código.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 O `Form1_Load` método no código anterior mostra o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procedimento geral para hospedar um controle:  
  
1. Crie um objeto <xref:System.Windows.Forms.Integration.ElementHost>.  
  
2. Defina a <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>do controle para .  
  
3. Adicione <xref:System.Windows.Forms.Integration.ElementHost> o controle <xref:System.Windows.Forms.Panel> à <xref:System.Windows.Forms.Control.Controls%2A> coleção do controle.  
  
4. Crie uma instância [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do controle.  
  
5. Hospede o controle composto no formulário atribuindo o <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> controle à propriedade do <xref:System.Windows.Forms.Integration.ElementHost> controle.  
  
 As duas linhas `Form1_Load` restantes no método anexam os manipuladores a dois eventos de controle:  
  
- `OnButtonClick`é um evento personalizado que é acionado pelo controle composto quando o usuário clica no botão **OK** ou **Cancel.** O evento é manipulado para obter a resposta do usuário e coletar os dados especificados por ele.  
  
- <xref:System.Windows.FrameworkElement.Loaded>é um evento padrão que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é levantado por um controle quando está totalmente carregado. O evento é usado aqui porque o exemplo precisa inicializar diversas variáveis globais usando propriedades do controle. No momento do evento <xref:System.Windows.Forms.Form.Load> do formulário, o controle não está totalmente carregado `null`e esses valores ainda estão definidos para . Você precisa esperar até que <xref:System.Windows.FrameworkElement.Loaded> o evento do controle ocorra antes de acessar essas propriedades.  
  
 O <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos é mostrado no código anterior. O `OnButtonClick` manipulador é discutido na próxima seção.  
  
### <a name="handling-onbuttonclick"></a>Manipulando o OnButtonClick  
 O `OnButtonClick` evento ocorre quando o usuário clica no botão **OK** ou **Cancel.**  
  
 O manipulador de eventos verifica `IsOK` o campo do argumento do evento para determinar qual botão foi clicado. As `lbl`variáveis *de* dados <xref:System.Windows.Forms.Label> correspondem aos controles discutidos anteriormente. Se o usuário clicar no botão **OK,** os <xref:System.Windows.Controls.TextBox> dados dos controles do <xref:System.Windows.Forms.Label> controle são atribuídos ao controle correspondente. Se o usuário clicar <xref:System.Windows.Forms.Label.Text%2A> **em Cancelar,** os valores serão definidos para as strings padrão.  
  
 Adicione o botão a seguir `Form1` clique no código do manipulador de eventos à classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Criar e executar o aplicativo. Adicione algum texto no controle composto wpf e clique em **OK**. O texto é exibido nos rótulos. Neste ponto, não foi adicionado um código para manipular os botões de opção.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modificando a aparência do controle  
 Os <xref:System.Windows.Forms.RadioButton> controles no formulário permitirão que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o usuário altere as cores de primeiro plano e de fundo do controle composto, bem como várias propriedades da fonte. A cor de fundo <xref:System.Windows.Forms.Integration.ElementHost> é exposta pelo objeto. As propriedades restantes são expostas como propriedades personalizadas do controle.  
  
 Clique duas <xref:System.Windows.Forms.RadioButton> vezes em cada <xref:System.Windows.Forms.RadioButton.CheckedChanged> controle no formulário para criar manipuladores de eventos. Substitua <xref:System.Windows.Forms.RadioButton.CheckedChanged> os manipuladores de eventos pelo seguinte código.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Criar e executar o aplicativo. Clique nos diferentes botões de opção para ver o efeito no controle composto do WPF.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Instruções passo a passo: hospedando um controle composto dos Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: hospedando um controle composto do WPF 3D no Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
