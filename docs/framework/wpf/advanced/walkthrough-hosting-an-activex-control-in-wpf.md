---
title: 'Instruções passo a passo: hospedando um controle ActiveX no WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 671138389b471ad9b9c62bd768895832d0324591
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540254"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Instruções passo a passo: hospedando um controle ActiveX no WPF
Para permitir uma melhor interação com navegadores, você pode usar controles [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] nos seus aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Essa instrução passo a passo demonstra como você pode hospedar o [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] como um controle em uma página [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criar o projeto.  
  
-   Criando o controle ActiveX.  
  
-   Hospedando o controle ActiveX em uma página do WPF.  
  
 Quando concluir este passo a passo, você entenderá como usar controles [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] no seu aplicativo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] instalado no computador em que o Visual Studio está instalado.  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
  
#### <a name="to-create-and-set-up-the-project"></a>Criar e configurar o projeto  
  
1.  Crie um projeto de aplicativo WPF chamado `HostingAxInWpf`.  
  
2.  Adicione um projeto de biblioteca de controle do Windows Forms à solução e nomeie-o como `WmpAxLib`.  
  
3.  No projeto WmpAxLib, adicione uma referência ao assembly do Windows Media Player, que é chamado wmp.dll.  
  
4.  Abra a **Caixa de Ferramentas**.  
  
5.  Clique com o botão direito do mouse na **Caixa de ferramentas** e, em seguida, clique em **Escolher Itens**.  
  
6.  Clique na guia **Componentes COM**, selecione o controle **Windows Media Player** e, em seguida, clique em **OK**.  
  
     O controle do Windows Media Player é adicionado para à **Caixa de ferramentas**.  
  
7.  No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo **UserControl1** e, em seguida, clique em **Renomear**.  
  
8.  Altere o nome para `WmpAxControl.vb` ou `WmpAxControl.cs`, dependendo da linguagem.  
  
9. Se for solicitado que você renomeie todas as referências, clique em **Sim**.  
  
## <a name="creating-the-activex-control"></a>Criando o controle ActiveX  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] gera automaticamente um <xref:System.Windows.Forms.AxHost> classe wrapper para um [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controlar quando o controle é adicionado a uma superfície de design. O procedimento a seguir cria um assembly gerenciado chamado AxInterop.WMPLib.dll.  
  
#### <a name="to-create-the-activex-control"></a>Criar o controle ActiveX  
  
1.  Abra WmpAxControl.vb ou WmpAxControl.cs no Designer de Formulários do Windows.  
  
2.  Na **Caixa de ferramentas**, adicione o controle do Windows Media Player para a superfície de design.  
  
3.  Na janela Propriedades, defina o valor do controle do Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Fill>.  
  
4.  Compile o projeto de biblioteca do controle WmpAxLib.  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hospedando o controle ActiveX em uma página do WPF  
  
#### <a name="to-host-the-activex-control"></a>Hospedar o controle ActiveX  
  
1.  No projeto HostingAxInWpf, adicione uma referência ao assembly de interoperabilidade [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] gerado.  
  
     Esse assembly é chamado AxInterop.WMPLib.dll e foi adicionado à pasta Debug do projeto WmpAxLib quando você importou o controle do Windows Media Player.  
  
2.  Adicione uma referência ao assembly WindowsFormsIntegration, que é chamado WindowsFormsIntegration.dll.  
  
3.  Adicione uma referência ao assembly [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], que é chamado de System.Windows.Forms.dll.  
  
4.  Abra o MainWindow.xaml no WPF Designer.  
  
5.  Nome do <xref:System.Windows.Controls.Grid> elemento `grid1`.  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  No modo de Design ou XAML, selecione o <xref:System.Windows.Window> elemento.  
  
7.  Na janela Propriedades, clique na guia **Eventos**.  
  
8.  Clique duas vezes o <xref:System.Windows.FrameworkElement.Loaded> eventos.  
  
9. Insira o seguinte código para manipular o <xref:System.Windows.FrameworkElement.Loaded> eventos.  
  
     Esse código cria uma instância das <xref:System.Windows.Forms.Integration.WindowsFormsHost> controlar e adiciona uma instância da `AxWindowsMediaPlayer` controle como seu filho.  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Pressione F5 para compilar e executar o aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [Passo a passo: hospedando um controle composto do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
