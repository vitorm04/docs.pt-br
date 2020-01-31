---
title: Hospedar um controle de Windows Forms no WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 5e994f65c0665a5726c4c8c19141da5ea3f5e6f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794177"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Instruções passo a passo: hospedando um controle dos Windows Forms no WPF

O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece muitos controles com um amplo conjunto de recursos. No entanto, às vezes você pode querer usar controles de Windows Forms em suas páginas de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Por exemplo, você pode ter um investimento substancial em controles de Windows Forms existentes ou pode ter um controle de Windows Forms que fornece funcionalidade exclusiva.

Este tutorial mostra como hospedar um Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> controle em uma página [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando código.

Para obter uma listagem de código completa das tarefas mostradas neste passo a passos, consulte [hospedando um controle de Windows Forms no exemplo do WPF](https://go.microsoft.com/fwlink/?LinkID=160057).

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

É necessário o Visual Studio para concluir este passo a passo.

## <a name="hosting-the-windows-forms-control"></a>Hospedando o controle dos Windows Forms

### <a name="to-host-the-maskedtextbox-control"></a>Para hospedar o controle MaskedTextBox

1. Crie um projeto de aplicativo WPF chamado `HostingWfInWpf`.

2. Adicione referências aos assemblies a seguir.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Abra o MainWindow.xaml no WPF Designer.

4. Nomeie o elemento de <xref:System.Windows.Controls.Grid> `grid1`.

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. No modo de exibição modo de exibição de Design ou XAML, selecione o elemento <xref:System.Windows.Window>.

6. Na janela Propriedades, clique na guia **Eventos**.

7. Clique duas vezes no evento <xref:System.Windows.FrameworkElement.Loaded>.

8. Insira o código a seguir para manipular o evento <xref:System.Windows.FrameworkElement.Loaded>.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. Na parte superior do arquivo, adicione o seguinte `Imports` ou `using` instrução.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Pressione **F5** para compilar e executar o aplicativo.

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Passo a passo: hospedando um controle do Windows Forms no WPF usando XAML](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Passo a passo: hospedando um controle composto do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: hospedando um controle composto do WPF no Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Controles dos Windows Forms e controles WPF equivalentes](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hospedando um controle de Windows Forms no exemplo do WPF](https://go.microsoft.com/fwlink/?LinkID=160057)
