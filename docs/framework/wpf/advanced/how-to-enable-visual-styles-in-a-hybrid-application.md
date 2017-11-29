---
title: "Como habilitar estilos visuais em um aplicativo híbrido"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e628835f0e5fb315f15b9e9946c48f7017092bae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Como habilitar estilos visuais em um aplicativo híbrido
Este tópico mostra como habilitar [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] estilos visuais em um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle hospedado em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-aplicativo com base em.  
  
 Se o aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método, a maioria das suas [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles usará automaticamente estilos visuais quando seu aplicativo é executado em [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]. Para obter mais informações, consulte [renderização de controles com estilos visuais](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Para uma listagem de código completa das tarefas ilustradas neste tópico, consulte [habilitar estilos visuais em um exemplo de aplicativo híbrido](http://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Habilitando estilos visuais no Windows Forms  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Para habilitar estilos visuais no Windows Forms  
  
1.  Criar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projeto de aplicativo chamado `HostingWfWithVisualStyles`.  
  
2.  No Gerenciador de Soluções, adicione referências aos assemblies a seguir.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Na caixa de ferramentas, clique duas vezes o <xref:System.Windows.Controls.Grid> ícone para colocar um <xref:System.Windows.Controls.Grid> elemento na superfície de design.  
  
4.  Na janela Propriedades, defina os valores da <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A> propriedades **automática**.  
  
5.  No modo de Design ou modo de exibição XAML, selecione a <xref:System.Windows.Window>.  
  
6.  Na janela Propriedades, clique na guia **Eventos**.  
  
7.  Clique duas vezes o <xref:System.Windows.FrameworkElement.Loaded> evento.
  
8.  Em MainWindow.xaml.vb ou MainWindow.xaml.cs, insira o seguinte código para manipular o <xref:System.Windows.FrameworkElement.Loaded> evento.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Pressione F5 para compilar e executar o aplicativo.  
  
     O [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle é pintado com estilos visuais.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Desabilitando estilos visuais do Windows Forms  
 Para desativar estilos visuais, simplesmente remova a chamada para o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Para desabilitar estilos visuais do Windows Forms  
  
1.  Abra MainWindow.xaml.vb ou MainWindow.xaml.cs no editor de código.  
  
2.  Comente a chamada para o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método.  
  
3.  Pressione F5 para compilar e executar o aplicativo.  
  
     O [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle é pintado com o estilo padrão do sistema.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Renderizando controles com estilos visuais](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [Passo a passo: hospedando um controle do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
