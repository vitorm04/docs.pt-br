---
title: "Instruções passo a passo: criando novo conteúdo WPF em Windows Forms na hora do design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc357b8ad1ff450c699878dfffe1fbb6e2440f49
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a>Instruções passo a passo: criando novo conteúdo WPF em Windows Forms na hora do design
Este tópico mostra como criar um controle do Windows Presentation Foundation (WPF) para uso em aplicativos baseados nos Windows Forms.  
  
 Nesta instrução passo a passo, as seguintes tarefas serão executadas:  
  
-   Crie o projeto.  
  
-   Criar um novo controle WPF.  
  
-   Adicionar o novo controle WPF a um formulário do Windows Form. O controle WPF é hospedado em um <xref:System.Windows.Forms.Integration.ElementHost> controle.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto dos Windows Forms.  
  
> [!NOTE]
>  Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
-   Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `HostingWpf`.  
  
## <a name="creating-a-new-wpf-control"></a>Criar um novo controle WPF  
 Criar um novo controle WPF e adicioná-lo ao projeto é tão fácil quanto adicionar qualquer outro item ao projeto. O Designer de Formulários do Windows funciona com um determinado tipo de controle, chamado *controle de composição* ou *controle de usuário*. Para obter mais informações sobre controles de usuário do WPF, consulte <xref:System.Windows.Controls.UserControl>.  
  
> [!NOTE]
>  O <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> de WPF é distinto do tipo de controle de usuário fornecido pelo Windows Forms, que também é chamado de tipo <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.  
  
#### <a name="to-create-a-new-wpf-control"></a>Criar um novo controle WPF  
  
1.  No **Gerenciador de Soluções**, adicione um novo projeto de **Biblioteca de Controle de Usuário do WPF** à solução. Use o nome padrão da biblioteca de controle, `WpfControlLibrary1`. O nome de controle padrão é `UserControl1.xaml`.  
  
     Adicionar o novo controle causa os seguintes efeitos.  
  
    -   O arquivo UserControl1.xaml será adicionado.  
  
    -   O arquivo UserControl1.xaml.cs ou UserControl1.xaml.vb será adicionado. Este arquivo contém o code-behind para manipuladores de eventos e outras implementações.  
  
    -   Referências a assemblies WPF serão adicionadas.  
  
    -   O arquivo UserControl1.xaml será aberto no [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].  
  
2.  No modo de exibição de Design, verifique se `UserControl1` está selecionado. Para obter mais informações, consulte [Como Selecionar e Mover Elementos na Superfície de Design](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades `200`.  
  
4.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle na superfície de design.  
  
5.  No **propriedades** janela, defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **conteúdo hospedado**.  
  
    > [!NOTE]
    >  No geral, é necessário hospedar conteúdos do WPF mais sofisticados. O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.  
  
6.  Compile o projeto.  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a>Adicionar um controle WPF a um formulário do Windows Form  
 O novo controle WPF está pronto para uso no formulário. Windows Forms usa o <xref:System.Windows.Forms.Integration.ElementHost> controle para hospedar conteúdo WPF  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a>Adicionar um controle WPF a um formulário do Windows Form  
  
1.  Abra `Form1` no Designer de Formulários do Windows.  
  
2.  Na **Caixa de Ferramentas**, localize a guia com o rótulo **Controles de Usuário WPF WPFUserControlLibrary**.  
  
3.  Arraste uma instância de `UserControl1` para o formulário.  
  
    -   Um <xref:System.Windows.Forms.Integration.ElementHost> controle é criado automaticamente no formulário para hospedar o controle WPF.  
  
    -   O <xref:System.Windows.Forms.Integration.ElementHost> controle é chamado de `elementHost1` e no **propriedades** janela, você pode ver sua <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> está definida como **UserControl1**.  
  
    -   Referências a assemblies WPF serão adicionadas ao projeto.  
  
    -   O controle `elementHost1` tem um painel de smart tag que mostra as opções de hospedagem disponíveis.  
  
4.  No painel de smart tag **ElementHost Tasks**, selecione **Encaixar no Contêiner Pai**.  
  
5.  Pressione F5 para compilar e executar o aplicativo.  
  
## <a name="next-steps"></a>Próximas etapas  
 O Windows Forms e o WPF são tecnologias diferentes, mas são projetados para interoperar estreitamente. Para oferecer uma aparência e um comportamento mais ricos em aplicativos, tente o seguinte.  
  
-   Hospedar um controle dos Windows Forms em uma página WPF. Para obter mais informações, consulte [Instruções Passo a Passo: Hospedando um Controle dos Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).  
  
-   Aplique estilos visuais dos Windows Forms ao conteúdo do WPF. Para obter mais informações, consulte [Como Habilitar Estilos Visuais em um Aplicativo Híbrido](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
-   Altere o estilo do conteúdo do WPF. Para obter mais informações, consulte [Instruções Passo a Passo: Definindo o Estilo do Conteúdo do WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migração e interoperabilidade](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Usando Controles do WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Designer do WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
