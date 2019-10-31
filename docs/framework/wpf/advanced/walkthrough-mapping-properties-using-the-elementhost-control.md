---
title: 'Instruções passo a passo: mapeando propriedades usando o controle ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 7d1cf353f7e6c4b87c13598e7e6029960cd0f715
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197820"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Instruções passo a passo: mapeando propriedades usando o controle ElementHost

Este passo a passos mostra como usar a propriedade <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> para mapear [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Propriedades para propriedades correspondentes em um elemento de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedado.

As tarefas ilustradas neste passo a passo incluem:

- Criar o projeto.

- Definir um novo mapeamento de propriedade.

- Remover um mapeamento de propriedade padrão.

- Estender um mapeamento de propriedade padrão.

Para ver uma listagem de código completa de todas tarefas ilustradas nesta instrução passo a passo, consulte [Mapeando propriedades usando o exemplo de controle ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).

Quando você terminar, poderá mapear propriedades [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] para as propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondentes em um elemento hospedado.

## <a name="prerequisites"></a>Prerequisites

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Visual Studio 2017

## <a name="creating-the-project"></a>Criando o Projeto

### <a name="to-create-the-project"></a>Para criar o projeto

1. Crie um projeto de **aplicativo Windows Forms** chamado `PropertyMappingWithElementHost`.

2. Em **Gerenciador de soluções**, adicione referências aos seguintes assemblies de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

    - PresentationCore

    - PresentationFramework

    - WindowsBase

    - WindowsFormsIntegration

3. Copie o seguinte código na parte superior do arquivo de código `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. Abra `Form1` no Designer de Formulários do Windows. Clique duas vezes no formulário para adicionar um manipulador de eventos para o evento <xref:System.Windows.Forms.Form.Load>.

5. Retorne ao Designer de Formulários do Windows e adicione um manipulador de eventos para o evento de <xref:System.Windows.Forms.Control.Resize> do formulário. Para obter mais informações, consulte [Como criar manipuladores de eventos usando o Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).

6. Declare um campo de <xref:System.Windows.Forms.Integration.ElementHost> na classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>Definindo novos mapeamentos de propriedade

O controle de <xref:System.Windows.Forms.Integration.ElementHost> fornece vários mapeamentos de propriedade padrão. Você adiciona um novo mapeamento de propriedade chamando o método <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>do controle de <xref:System.Windows.Forms.Integration.ElementHost>.

### <a name="to-define-new-property-mappings"></a>Definir novos mapeamentos de propriedade

1. Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     O método `AddMarginMapping` adiciona um novo mapeamento para a propriedade <xref:System.Windows.Forms.Control.Margin%2A>.

     O método `OnMarginChange` converte a propriedade <xref:System.Windows.Forms.Control.Margin%2A> para a propriedade [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A>.

2. Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     O método `AddRegionMapping` adiciona um novo mapeamento para a propriedade <xref:System.Windows.Forms.Control.Region%2A>.

     O método `OnRegionChange` converte a propriedade <xref:System.Windows.Forms.Control.Region%2A> para a propriedade [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A>.

     O método `Form1_Resize` manipula o evento de <xref:System.Windows.Forms.Control.Resize> do formulário e dimensiona a região de recorte para se ajustar ao elemento hospedado.

## <a name="removing-a-default-property-mapping"></a>Removendo um mapeamento de propriedade padrão

Remova um mapeamento de propriedade padrão chamando o método <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>do controle de <xref:System.Windows.Forms.Integration.ElementHost>.

### <a name="to-remove-a-default-property-mapping"></a>Remover um mapeamento de propriedade padrão

- Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     O método `RemoveCursorMapping` exclui o mapeamento padrão para a propriedade <xref:System.Windows.Forms.Control.Cursor%2A>.

## <a name="extending-a-default-property-mapping"></a>Estendendo um mapeamento de propriedade padrão

Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.

### <a name="to-extend-a-default-property-mapping"></a>Estender um mapeamento de propriedade padrão

- Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     O método `ExtendBackColorMapping` adiciona um tradutor de propriedade personalizada ao mapeamento de propriedade <xref:System.Windows.Forms.Control.BackColor%2A> existente.

     O método `OnBackColorChange` atribui uma imagem específica à propriedade <xref:System.Windows.Controls.Control.Background%2A> do controle hospedado. O método `OnBackColorChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.

## <a name="initialize-your-property-mappings"></a>Inicializar os mapeamentos de propriedade

1. Copie o código a seguir para a definição da classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     O método `Form1_Load` manipula o evento <xref:System.Windows.Forms.Form.Load> e executa a inicialização a seguir.

    - Cria um elemento de <xref:System.Windows.Controls.Button> de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

    - Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.

    - Atribui valores iniciais para as propriedades mapeadas.

2. Pressione F5 para compilar e executar o aplicativo.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md)
- [Criar o XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Passo a passo: hospedando um controle composto do WPF no Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
