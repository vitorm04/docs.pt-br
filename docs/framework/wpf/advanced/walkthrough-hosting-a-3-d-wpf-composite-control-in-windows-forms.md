---
title: 'Passo a passo: Hospedando um controle composto do WPF 3D nos Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: b4c5001e671db9d615f3bcbc0a35b7b36b45bb01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506856"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Passo a passo: Hospedando um controle composto do WPF 3D nos Windows Forms

Este passo a passo demonstra como você pode criar uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composto controlar e hospedá-lo no [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles e formulários usando o <xref:System.Windows.Forms.Integration.ElementHost> controle.

Neste passo a passo, você implementará uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> que contém dois controles filho. O <xref:System.Windows.Controls.UserControl> exibe um cone tridimensional (3D). É muito mais fácil renderizar objetos 3D com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que com [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Portanto, faz sentido para hospedar uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> classe para criar gráficos 3D em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

As tarefas ilustradas neste passo a passo incluem:

-   Criando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

-   Criando o projeto de host do Windows Forms.

-   Hospedando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Pré-requisitos

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

-   Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>Criar o UserControl

1.  Criar uma **biblioteca de controle de usuário do WPF** projeto chamado `HostingWpfUserControlInWf`.

2.  Abra UserControl1.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

3.  Substitua o código gerado pelo código a seguir:

     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Esse código define uma <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> que contém dois controles filho. O primeiro controle filho é um <xref:System.Windows.Controls.Label?displayProperty=nameWithType> controle; o segundo é um <xref:System.Windows.Controls.Viewport3D> controle que exibe um cone 3D.

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>Criar o projeto de host

1.  Adicionar um **aplicativo WPF (.NET Framework)** projeto chamado `WpfUserControlHost` à solução. Para obter mais informações, confira [Como: Criar um novo projeto de aplicativo do WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).

2.  Na **Gerenciador de soluções**, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado WindowsFormsIntegration.

3.  Adicione referências aos assemblies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a seguir:

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

4.  Adicione uma referência ao projeto `HostingWpfUserControlInWf`.

5.  No Gerenciador de Soluções, defina o projeto `WpfUserControlHost` como o projeto de inicialização.

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>Hospedar o UserControl

1.  No Designer de Formulários do Windows, abra Form1.

2.  Na janela Propriedades, clique em **eventos**e, em seguida, clique duas vezes o <xref:System.Windows.Forms.Form.Load> evento para criar um manipulador de eventos.

     O Editor de Código abre o manipulador de eventos `Form1_Load` recém gerado.

3.  Substitua o código em Form1.cs pelo código a seguir.

     O `Form1_Load` manipulador de eventos cria uma instância do `UserControl1` e a adiciona ao <xref:System.Windows.Forms.Integration.ElementHost> coleção de controles filho do controle. O <xref:System.Windows.Forms.Integration.ElementHost> controle é adicionado à coleção do formulário de controles filho.

     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4.  Pressione **F5** para compilar e executar o aplicativo.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Passo a passo: Hospedando um controle composto do WPF nos Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Passo a passo: Hospedando um controle composto do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Hospedando um controle composto do WPF nos exemplo do Windows Forms](https://go.microsoft.com/fwlink/?LinkID=160001)