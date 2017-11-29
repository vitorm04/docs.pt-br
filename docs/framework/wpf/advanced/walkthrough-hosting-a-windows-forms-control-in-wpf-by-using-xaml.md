---
title: "Instruções passo a passo: hospedando um controle dos Windows Forms no WPF usando XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5fe01b4ef9aebe697138e925935b73bd4770e86a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>Instruções passo a passo: hospedando um controle dos Windows Forms no WPF usando XAML
O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece muitos controles com um amplo conjunto de recursos. No entanto, às vezes, convém usar controles do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em suas páginas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Por exemplo, você pode ter um investimento substancial em controles existentes do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou pode ter um controle do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] que fornece funcionalidade exclusiva.  
  
 Este passo a passo mostra como hospedar um Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Para uma listagem de código completa de todas as tarefas mostradas neste passo a passo, veja [Hospedando um controle dos Windows Forms no WPF usando exemplo XAML](http://go.microsoft.com/fwlink/?LinkID=160000).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="hosting-the-windows-forms-control"></a>Hospedando o controle dos Windows Forms  
  
#### <a name="to-host-the-maskedtextbox-control"></a>Para hospedar o controle MaskedTextBox  
  
1.  Crie um projeto de aplicativo WPF chamado `HostingWfInWpfWithXaml`.  
  
2.  Adicione referências aos assemblies a seguir.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Abra MainWindow.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  No <xref:System.Windows.Window> elemento, adicione o seguinte mapeamento de namespace. O mapeamento de namespace `wf` estabelece uma referência ao assembly que contém o controle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  No <xref:System.Windows.Controls.Grid> elemento adicionar o XAML a seguir.  
  
     O <xref:System.Windows.Forms.MaskedTextBox> controle é criado como um filho de <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle.  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  Pressione F5 para compilar e executar o aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Designer do WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Passo a passo: hospedando um controle do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [Passo a passo: hospedando um controle composto do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Passo a passo: hospedando um controle composto do WPF no Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Controles dos Windows Forms e controles WPF equivalentes](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [Hospedando um controle dos Windows Forms no WPF usando um exemplo XAML](http://go.microsoft.com/fwlink/?LinkID=160000)
