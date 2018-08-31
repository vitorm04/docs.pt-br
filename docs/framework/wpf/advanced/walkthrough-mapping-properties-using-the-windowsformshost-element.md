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
ms.openlocfilehash: 77027d771cf471e563e24c46d7794a18ad223541
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258512"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Instruções passo a passo: mapeando propriedades usando o elemento WindowsFormsHost

Este passo a passo mostra como usar o <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> propriedade para mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades às propriedades correspondentes em um hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.

As tarefas ilustradas neste passo a passo incluem:

-   Criar o projeto.

-   Definir o layout do aplicativo.

-   Definir um novo mapeamento de propriedade.

-   Remover um mapeamento de propriedade padrão.

-   Substituir um mapeamento de propriedade padrão.

-   Estender um mapeamento de propriedade padrão.

Para obter uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [mapeando propriedades usando o exemplo de elemento WindowsFormsHost](http://go.microsoft.com/fwlink/?LinkID=160019).

Quando tiver terminado, você será capaz de mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades às propriedades correspondentes em um hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.

## <a name="prerequisites"></a>Pré-requisitos

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

-   Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Criar e configurar o projeto

1.  Criar uma **aplicativo WPF** projeto chamado `PropertyMappingWithWfhSample`.

2.  Na **Gerenciador de soluções**, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado WindowsFormsIntegration.

3.  Na **Gerenciador de soluções**, adicione referências aos assemblies System. Drawing e System.

## <a name="defining-the-application-layout"></a>Definindo o layout do aplicativo

O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-com base em aplicativo usa o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento host um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.

### <a name="to-define-the-application-layout"></a>Definir o layout do aplicativo

1.  Abra Window1.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2.  Substitua o código existente pelo código a seguir.

     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3.  Abra Window1.xaml.cs no Editor de Código.

4.  Na parte superior do arquivo, importe os seguintes namespaces.

     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Definindo um novo mapeamento de propriedade

O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento fornece o padrão de vários mapeamentos de propriedade. Adicionar um novo mapeamento de propriedade chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método em de <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-define-a-new-property-mapping"></a>Definir um novo mapeamento de propriedade

-   Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     O `AddClipMapping` método adiciona um novo mapeamento para o <xref:System.Windows.UIElement.Clip%2A> propriedade.

     O `OnClipChange` método traduz a <xref:System.Windows.UIElement.Clip%2A> propriedade para o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> propriedade.

     O `Window1_SizeChanged` método lida com a janela <xref:System.Windows.FrameworkElement.SizeChanged> eventos e dimensiona a região de recorte para caber na janela do aplicativo.

## <a name="removing-a-default-property-mapping"></a>Removendo um mapeamento de propriedade padrão

Remover um mapeamento de propriedade padrão chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> método em de <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-remove-a-default-property-mapping"></a>Remover um mapeamento de propriedade padrão

-   Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     O `RemoveCursorMapping` método exclui o mapeamento padrão para o <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade.

## <a name="replacing-a-default-property-mapping"></a>Substituindo um mapeamento de propriedade padrão

Substituir um mapeamento de propriedade padrão removendo o mapeamento padrão e chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método em de <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-replace-a-default-property-mapping"></a>Substituir um mapeamento de propriedade padrão

-   Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     O `ReplaceFlowDirectionMapping` método substitui o mapeamento padrão para o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade.

     O `OnFlowDirectionChange` método traduz a <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade para o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> propriedade.

     O `cb_CheckedChanged` identificadores de método de <xref:System.Windows.Forms.CheckBox.CheckedChanged> evento no <xref:System.Windows.Forms.CheckBox> controle. Ele atribui a <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade com base no valor da <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriedade

## <a name="extending-a-default-property-mapping"></a>Estendendo um mapeamento de propriedade padrão

Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.

### <a name="to-extend-a-default-property-mapping"></a>Estender um mapeamento de propriedade padrão

-   Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     O `ExtendBackgroundMapping` método adiciona um tradutor de propriedade personalizada para existente <xref:System.Windows.Controls.Control.Background%2A> mapeamento de propriedade.

     O `OnBackgroundChange` método atribui uma imagem específica para o controle hospedado <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade. O método `OnBackgroundChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.

## <a name="initializing-your-property-mappings"></a>Inicializando seus mapeamentos de propriedades

Configure seus mapeamentos de propriedades chamando os métodos descritos anteriormente no <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos.

### <a name="to-initialize-your-property-mappings"></a>Inicializar seus mapeamentos de propriedades

1.  Copie o código a seguir para a definição da classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     O `WindowLoaded` identificadores de método a <xref:System.Windows.FrameworkElement.Loaded> eventos e realiza a seguinte inicialização.

    -   Cria uma [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> controle.

    -   Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.

    -   Atribui valores iniciais para as propriedades mapeadas.

2.  Pressione **F5** para compilar e executar o aplicativo. Clique na caixa de seleção para ver o efeito do <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapeamento. Ao clicar na caixa de seleção, o layout inverte sua orientação esquerda-direita.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms e mapeamento de propriedade do WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Passo a passo: hospedando um controle do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)