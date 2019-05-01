---
title: 'Passo a passo: hospedar um controle do Windows Forms no WPF usando XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 10554145de9725bb4cfc655ed88195dce28d739c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032104"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>Passo a passo: hospedar um controle do Windows Forms no WPF usando XAML
O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece muitos controles com um amplo conjunto de recursos. No entanto, às vezes, convém usar controles do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em suas páginas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Por exemplo, você pode ter um investimento substancial em controles existentes do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou pode ter um controle do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] que fornece funcionalidade exclusiva.  
  
 Este passo a passo mostra como hospedar um Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Para uma listagem de código completa de todas as tarefas mostradas neste passo a passo, veja [Hospedando um controle dos Windows Forms no WPF usando exemplo XAML](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).
  
## <a name="prerequisites"></a>Pré-requisitos  

É necessário o Visual Studio para concluir este passo a passo.  
  
## <a name="hosting-the-windows-forms-control"></a>Hospedando o controle dos Windows Forms  
  
#### <a name="to-host-the-maskedtextbox-control"></a>Para hospedar o controle MaskedTextBox  
  
1. Crie um projeto de aplicativo WPF chamado `HostingWfInWpfWithXaml`.  
  
2. Adicione referências aos assemblies a seguir.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. Abra MainWindow.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4. No <xref:System.Windows.Window> elemento, adicione o seguinte mapeamento de namespace. O `wf` mapeamento de namespace estabelece uma referência ao assembly que contém o controle de formulários do Windows.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. No <xref:System.Windows.Controls.Grid> elemento adicionar o XAML a seguir.  
  
     O <xref:System.Windows.Forms.MaskedTextBox> controle é criado como um filho de <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle.  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. Pressione F5 para compilar e executar o aplicativo.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Passo a passo: Hospedando um controle de formulários do Windows no WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto do WPF nos Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Controles dos Windows Forms e controles WPF equivalentes](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hospedando um controle dos Windows Forms no WPF usando um exemplo XAML](https://go.microsoft.com/fwlink/?LinkID=160000)
