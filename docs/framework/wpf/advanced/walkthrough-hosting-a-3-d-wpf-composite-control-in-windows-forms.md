---
title: 'Instruções passo a passo: hospedando um controle composto do WPF 3D nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: a9aca5d1aff1057d85509be517bb352b4b27bf9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548201"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Instruções passo a passo: hospedando um controle composto do WPF 3D nos Windows Forms
Este passo a passo demonstra como você pode criar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composto controlar e hospedá-lo em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles e formulários usando o <xref:System.Windows.Forms.Integration.ElementHost> controle.  
  
 Neste passo a passo, você irá implementar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> que contém dois controles filho. O <xref:System.Windows.Controls.UserControl> exibe um cone tridimensional (3D). É muito mais fácil renderizar objetos 3D com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que com [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Portanto, faz sentido para hospedar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> classe para criar gráficos 3D em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.  
  
-   Criando o projeto de host do Windows Forms.  
  
-   Hospedando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.  
  
 Para ver uma listagem de código completa das tarefas ilustradas nesta instrução passo a passo, consulte [Exemplo de hospedagem de um controle composto 3D do WPF no Windows Forms](http://go.microsoft.com/fwlink/?LinkID=160001).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a>Criando o UserControl  
  
#### <a name="to-create-the-usercontrol"></a>Criar o UserControl  
  
1.  Criar um projeto de biblioteca de controle de usuário de WPF chamada `HostingWpfUserControlInWf`.  
  
2.  Abra UserControl1.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
3.  Substitua o código gerado pelo código a seguir.  
  
     Esse código define uma <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> que contém dois controles filho. O primeiro controle filho é um <xref:System.Windows.Controls.Label?displayProperty=nameWithType> controle; o segundo é um <xref:System.Windows.Controls.Viewport3D> controle que exibe um cone 3D.  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a>Criando o projeto de host do Windows Forms  
  
#### <a name="to-create-the-host-project"></a>Criar o projeto de host  
  
1.  Adicione um projeto de Aplicativos do Windows chamado `WpfUserControlHost` à solução. Para obter mais informações, consulte [Como criar um novo projeto de aplicativo do WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  No Gerenciador de Soluções, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado de WindowsFormsIntegration.dll.  
  
3.  Adicione referências aos assemblies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a seguir:  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
4.  Adicione uma referência ao projeto `HostingWpfUserControlInWf`.  
  
5.  No Gerenciador de Soluções, defina o projeto `WpfUserControlHost` como o projeto de inicialização.  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a>Hospedando o UserControl do Windows Presentation Foundation  
  
#### <a name="to-host-the-usercontrol"></a>Hospedar o UserControl  
  
1.  No Designer de Formulários do Windows, abra Form1.  
  
2.  Na janela Propriedades, clique em **eventos**e, em seguida, clique duas vezes o <xref:System.Windows.Forms.Form.Load> evento para criar um manipulador de eventos.  
  
     O Editor de Código abre o manipulador de eventos `Form1_Load` recém gerado.  
  
3.  Substitua o código em Form1.cs pelo código a seguir.  
  
     O `Form1_Load` manipulador de eventos cria uma instância de `UserControl1` e adiciona a forma de <xref:System.Windows.Forms.Integration.ElementHost> coleção de controles filho do controle. O <xref:System.Windows.Forms.Integration.ElementHost> controle é adicionado à coleção do formulário de controles filho.  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  Pressione F5 para compilar e executar o aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Designer do WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Passo a passo: hospedando um controle composto do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Hospedando um controle composto do WPF nos exemplo do Windows Forms](http://go.microsoft.com/fwlink/?LinkID=160001)
