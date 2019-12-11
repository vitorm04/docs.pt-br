---
title: Como habilitar estilos visuais em um aplicativo híbrido
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 251c53a8665d2eae7c3b5bb23b0a388009362dcc
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960120"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Como habilitar estilos visuais em um aplicativo híbrido
Este tópico mostra como habilitar estilos visuais em um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado em um aplicativo baseado em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Se seu aplicativo chamar o método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, a maioria dos seus controles de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] usará automaticamente estilos visuais. Saiba mais em [Renderizar controles com estilos visuais](../../winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Para obter uma listagem de código completa das tarefas ilustradas neste tópico, consulte [habilitando estilos visuais em um exemplo de aplicativo híbrido](https://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Habilitando estilos visuais no Windows Forms  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Para habilitar estilos visuais no Windows Forms  
  
1. Crie um projeto de aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamado `HostingWfWithVisualStyles`.  
  
2. No Gerenciador de Soluções, adicione referências aos assemblies a seguir.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. Na caixa de ferramentas, clique duas vezes no ícone de <xref:System.Windows.Controls.Grid> para posicionar um elemento de <xref:System.Windows.Controls.Grid> na superfície de design.  
  
4. Na janela Propriedades, defina os valores das propriedades <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A> como **automático**.  
  
5. Na exibição modo de exibição de Design ou XAML, selecione o <xref:System.Windows.Window>.  
  
6. Na janela Propriedades, clique na guia **Eventos**.  
  
7. Clique duas vezes no evento <xref:System.Windows.FrameworkElement.Loaded>.
  
8. Em MainWindow. XAML. vb ou MainWindow.xaml.cs, insira o código a seguir para manipular o evento de <xref:System.Windows.FrameworkElement.Loaded>.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Pressione F5 para compilar e executar o aplicativo.  
  
     O controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é pintado com estilos visuais.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Desabilitando estilos visuais do Windows Forms  
 Para desabilitar os estilos visuais, basta remover a chamada para o método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Para desabilitar estilos visuais do Windows Forms  
  
1. Abra MainWindow.xaml.vb ou MainWindow.xaml.cs no editor de código.  
  
2. Comente a chamada para o método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
3. Pressione F5 para compilar e executar o aplicativo.  
  
     O controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é pintado com o estilo de sistema padrão.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Renderizando controles com estilos visuais](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [Passo a passo: hospedando um controle do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
