---
title: 'Passo a passo: mapear propriedades usando o controle ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 360f19e558f97e1807b329ad18e429fa893bbf86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053152"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Passo a passo: mapear propriedades usando o controle ElementHost

Este passo a passo mostra como usar o <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> propriedade para mapear [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] propriedades às propriedades correspondentes em um hospedado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento.

As tarefas ilustradas neste passo a passo incluem:

- Criar o projeto.

- Definir um novo mapeamento de propriedade.

- Remover um mapeamento de propriedade padrão.

- Estender um mapeamento de propriedade padrão.

Para ver uma listagem de código completa de todas tarefas ilustradas nesta instrução passo a passo, consulte [Mapeando propriedades usando o exemplo de controle ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).

Quando você terminar, poderá mapear propriedades [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] para as propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondentes em um elemento hospedado.

## <a name="prerequisites"></a>Pré-requisitos

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Visual Studio 2017

## <a name="creating-the-project"></a>Criando o Projeto

### <a name="to-create-the-project"></a>Para criar o projeto

1. Criar uma **aplicativo do Windows Forms** projeto chamado `PropertyMappingWithElementHost`.

2. Na **Gerenciador de soluções**, adicione referências para os seguintes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.

    - PresentationCore

    - PresentationFramework

    - WindowsBase

    - WindowsFormsIntegration

3. Copie o seguinte código na parte superior do arquivo de código `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. Abra `Form1` no Designer de Formulários do Windows. Clique duas vezes no formulário para adicionar um manipulador de eventos para o <xref:System.Windows.Forms.Form.Load> eventos.

5. Retorne ao Designer de formulários do Windows e adicionar um manipulador de eventos para o formulário <xref:System.Windows.Forms.Control.Resize> eventos. Para obter mais informações, confira [Como: Criar manipuladores de eventos usando o Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).

6. Declarar uma <xref:System.Windows.Forms.Integration.ElementHost> campo o `Form1` classe.

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>Definindo novos mapeamentos de propriedade

O <xref:System.Windows.Forms.Integration.ElementHost> controle fornece vários padrão mapeamentos de propriedade. Adicionar um novo mapeamento de propriedade chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método em de <xref:System.Windows.Forms.Integration.ElementHost> do controle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.

### <a name="to-define-new-property-mappings"></a>Definir novos mapeamentos de propriedade

1. Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     O `AddMarginMapping` método adiciona um novo mapeamento para o <xref:System.Windows.Forms.Control.Margin%2A> propriedade.

     O `OnMarginChange` método traduz a <xref:System.Windows.Forms.Control.Margin%2A> propriedade para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> propriedade.

2. Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     O `AddRegionMapping` método adiciona um novo mapeamento para o <xref:System.Windows.Forms.Control.Region%2A> propriedade.

     O `OnRegionChange` método traduz a <xref:System.Windows.Forms.Control.Region%2A> propriedade para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> propriedade.

     O `Form1_Resize` método lida com o formulário <xref:System.Windows.Forms.Control.Resize> eventos e dimensiona a região de recorte para caber no elemento hospedado.

## <a name="removing-a-default-property-mapping"></a>Removendo um mapeamento de propriedade padrão

Remover um mapeamento de propriedade padrão chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> método em de <xref:System.Windows.Forms.Integration.ElementHost> do controle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.

### <a name="to-remove-a-default-property-mapping"></a>Remover um mapeamento de propriedade padrão

- Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     O `RemoveCursorMapping` método exclui o mapeamento padrão para o <xref:System.Windows.Forms.Control.Cursor%2A> propriedade.

## <a name="extending-a-default-property-mapping"></a>Estendendo um mapeamento de propriedade padrão

Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.

### <a name="to-extend-a-default-property-mapping"></a>Estender um mapeamento de propriedade padrão

- Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     O `ExtendBackColorMapping` método adiciona um tradutor de propriedade personalizada para existente <xref:System.Windows.Forms.Control.BackColor%2A> mapeamento de propriedade.

     O `OnBackColorChange` método atribui uma imagem específica para o controle hospedado <xref:System.Windows.Controls.Control.Background%2A> propriedade. O método `OnBackColorChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.

## <a name="initialize-your-property-mappings"></a>Inicializar seus mapeamentos de propriedades

1. Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     O `Form1_Load` identificadores de método a <xref:System.Windows.Forms.Form.Load> eventos e realiza a seguinte inicialização.

    - Cria uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elemento.

    - Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.

    - Atribui valores iniciais para as propriedades mapeadas.

2. Pressione F5 para compilar e executar o aplicativo.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md)
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Passo a passo: Hospedando um controle composto do WPF nos Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)