---
title: 'Instruções passo a passo: mapeando propriedades usando o elemento WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: 94d175ec58f35b7e807786c221437d05c605c0bc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974221"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Instruções passo a passo: mapeando propriedades usando o elemento WindowsFormsHost

Este passo a passos mostra como usar a propriedade <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> para mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Propriedades para propriedades correspondentes em um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado.

As tarefas ilustradas neste passo a passo incluem:

- Criar o projeto.

- Definir o layout do aplicativo.

- Definir um novo mapeamento de propriedade.

- Remover um mapeamento de propriedade padrão.

- Substituir um mapeamento de propriedade padrão.

- Estender um mapeamento de propriedade padrão.

Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [mapeando propriedades usando o exemplo do elemento WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).

Quando tiver terminado, você poderá mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Propriedades para as propriedades correspondentes em um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado.

## <a name="prerequisites"></a>Prerequisites

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Criar e configurar o projeto

1. Crie um projeto de **aplicativo do WPF** chamado `PropertyMappingWithWfhSample`.

2. Em **Gerenciador de soluções**, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado de WindowsFormsIntegration. dll.

3. Em **Gerenciador de soluções**, adicione referências aos assemblies System. Drawing e System. Windows. Forms.

## <a name="defining-the-application-layout"></a>Definindo o layout do aplicativo

O aplicativo baseado em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]usa o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> para hospedar um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

### <a name="to-define-the-application-layout"></a>Definir o layout do aplicativo

1. Abra o Window1. XAML no designer do WPF.

2. Substitua o código existente pelo código a seguir.

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. Abra Window1.xaml.cs no Editor de Código.

4. Na parte superior do arquivo, importe os seguintes namespaces.

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Definindo um novo mapeamento de propriedade

O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> fornece vários mapeamentos de propriedade padrão. Você adiciona um novo mapeamento de propriedade chamando o método <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-define-a-new-property-mapping"></a>Definir um novo mapeamento de propriedade

- Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     O método `AddClipMapping` adiciona um novo mapeamento para a propriedade <xref:System.Windows.UIElement.Clip%2A>.

     O método `OnClipChange` converte a propriedade <xref:System.Windows.UIElement.Clip%2A> para a propriedade [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>.

     O método `Window1_SizeChanged` manipula o evento de <xref:System.Windows.FrameworkElement.SizeChanged> da janela e dimensiona a região de recorte para ajustá-la à janela do aplicativo.

## <a name="removing-a-default-property-mapping"></a>Removendo um mapeamento de propriedade padrão

Remova um mapeamento de propriedade padrão chamando o método <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-remove-a-default-property-mapping"></a>Remover um mapeamento de propriedade padrão

- Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     O método `RemoveCursorMapping` exclui o mapeamento padrão para a propriedade <xref:System.Windows.FrameworkElement.Cursor%2A>.

## <a name="replacing-a-default-property-mapping"></a>Substituindo um mapeamento de propriedade padrão

Substitua um mapeamento de propriedade padrão removendo o mapeamento padrão e chamando o método <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-replace-a-default-property-mapping"></a>Substituir um mapeamento de propriedade padrão

- Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     O método `ReplaceFlowDirectionMapping` substitui o mapeamento padrão para a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A>.

     O método `OnFlowDirectionChange` converte a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A> para a propriedade [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A>.

     O método `cb_CheckedChanged` manipula o evento <xref:System.Windows.Forms.CheckBox.CheckedChanged> no controle de <xref:System.Windows.Forms.CheckBox>. Ele atribui a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A> com base no valor da propriedade <xref:System.Windows.Forms.CheckBox.CheckState%2A>

## <a name="extending-a-default-property-mapping"></a>Estendendo um mapeamento de propriedade padrão

Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.

### <a name="to-extend-a-default-property-mapping"></a>Estender um mapeamento de propriedade padrão

- Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     O método `ExtendBackgroundMapping` adiciona um tradutor de propriedade personalizada ao mapeamento de propriedade <xref:System.Windows.Controls.Control.Background%2A> existente.

     O método `OnBackgroundChange` atribui uma imagem específica à propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> do controle hospedado. O método `OnBackgroundChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.

## <a name="initializing-your-property-mappings"></a>Inicializando seus mapeamentos de propriedades

Configure os mapeamentos de propriedade chamando os métodos descritos anteriormente no manipulador de eventos <xref:System.Windows.FrameworkElement.Loaded>.

### <a name="to-initialize-your-property-mappings"></a>Inicializar seus mapeamentos de propriedades

1. Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     O método `WindowLoaded` manipula o evento <xref:System.Windows.FrameworkElement.Loaded> e executa a inicialização a seguir.

    - Cria um controle de <xref:System.Windows.Forms.CheckBox> de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

    - Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.

    - Atribui valores iniciais para as propriedades mapeadas.

2. Pressione **F5** para compilar e executar o aplicativo. Clique na caixa de seleção para ver o efeito do mapeamento de <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Ao clicar na caixa de seleção, o layout inverte sua orientação esquerda-direita.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md)
- [Criar o XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Passo a passo: hospedando um controle do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
