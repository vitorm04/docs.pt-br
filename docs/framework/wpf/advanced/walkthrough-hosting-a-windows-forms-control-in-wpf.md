---
title: 'Passo a passo: Hospedando um controle de formulários do Windows no WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 8ef13ef89072f91c847a05facbcce344dda6ade2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374876"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Passo a passo: Hospedando um controle de formulários do Windows no WPF

O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece muitos controles com um amplo conjunto de recursos. No entanto, às vezes, convém usar controles do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em suas páginas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Por exemplo, você pode ter um investimento substancial em controles existentes do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou pode ter um controle do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] que fornece funcionalidade exclusiva.

Este passo a passo mostra como hospedar um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página por meio de código.

Para obter uma listagem de código completa das tarefas mostradas neste passo a passo, consulte [hospedando um controle de formulários do Windows no WPF de exemplo](https://go.microsoft.com/fwlink/?LinkID=160057).

## <a name="prerequisites"></a>Pré-requisitos

É necessário o Visual Studio para concluir este passo a passo.

## <a name="hosting-the-windows-forms-control"></a>Hospedando o controle dos Windows Forms

### <a name="to-host-the-maskedtextbox-control"></a>Para hospedar o controle MaskedTextBox

1.  Crie um projeto de aplicativo WPF chamado `HostingWfInWpf`.

2.  Adicione referências aos assemblies a seguir.

    -   WindowsFormsIntegration

    -   System.Windows.Forms

3.  Abra MainWindow.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

4.  Nome do <xref:System.Windows.Controls.Grid> elemento `grid1`.

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5.  No modo de Design ou XAML, selecione o <xref:System.Windows.Window> elemento.

6.  Na janela Propriedades, clique na guia **Eventos**.

7.  Clique duas vezes o <xref:System.Windows.FrameworkElement.Loaded> eventos.

8.  Insira o seguinte código para manipular o <xref:System.Windows.FrameworkElement.Loaded> eventos.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. Na parte superior do arquivo, adicione o seguinte `Imports` ou `using` instrução.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Pressione **F5** para compilar e executar o aplicativo.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Passo a passo: Hospedando um controle de formulários do Windows no WPF usando XAML](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Passo a passo: Hospedando um controle composto do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto do WPF nos Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Controles dos Windows Forms e controles WPF equivalentes](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hospedando um controle de formulários do Windows no WPF de exemplo](https://go.microsoft.com/fwlink/?LinkID=160057)
