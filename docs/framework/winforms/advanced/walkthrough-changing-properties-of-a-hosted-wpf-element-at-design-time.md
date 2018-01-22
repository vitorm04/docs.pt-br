---
title: "Instruções passo a passo: alterando propriedades de um elemento WPF hospedado no tempo de design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46b80ee0c74da7371ac8f7a16d3430b5b753059d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a>Instruções passo a passo: alterando propriedades de um elemento WPF hospedado no tempo de design
Este passo a passo mostra como alterar os valores de propriedade de um controle WPF (Windows Presentation Foundation) hospedado em um formulário do Windows Form.  
  
 Nesta instrução passo a passo, as seguintes tarefas serão executadas:  
  
-   Crie o projeto.  
  
-   Crie o controle WPF.  
  
-   Hospede os controles WPF em um formulário do Windows Form.  
  
-   Use o WPF Designer do Visual Studio para alterar valores de propriedade.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto dos Windows Forms.  
  
> [!NOTE]
>  Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
-   Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `WpfHost`.  
  
## <a name="creating-the-wpf-control"></a>Criando o controle WPF  
 Depois de adicionar um controle WPF ao projeto, você pode organizá-lo no formulário.  
  
#### <a name="to-create-wpf-controls"></a>Para criar controles WPF  
  
1.  Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao projeto. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  No **propriedades** janela, defina o valor da <xref:System.Windows.Controls.Control.Background%2A> propriedade `Blue`.  
  
3.  Compile o projeto.  
  
## <a name="changing-property-values-on-the-wpf-control"></a>Alterando os valores de propriedade no controle do WPF  
 O <xref:System.Windows.Forms.Integration.ElementHost> marca inteligente torna mais fácil alterar as propriedades de WPF hospedado conteúdo usando o Designer do WPF.  
  
#### <a name="to-host-a-wpf-control"></a>Para hospedar um controle WPF  
  
1.  Abra `Form1` no Designer de Formulários do Windows.  
  
2.  Na **Caixa de ferramentas**, na guia **Controles de usuário do WPF**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.  
  
     A instância do `UserControl1` está hospedada em um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.  
  
3.  No painel de smart tag **ElementHost Tasks**, selecione **Editar conteúdo hospedado**.  
  
     O UserControl1.xaml se abre no Designer do WPF.  
  
4.  No **propriedades** janela, defina o valor da <xref:System.Windows.Controls.Control.Background%2A> propriedade `Red`.  
  
5.  Recompile o projeto.  
  
6.  Abra `Form1` no Designer de Formulários do Windows.  
  
     A instância do `UserControl1` tem uma tela de fundo vermelha.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Como ancorar e encaixar controles filho em um controle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Como alinhar um controle às bordas de formulários no tempo de design](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migração e interoperabilidade](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Usando Controles do WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Designer do WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
