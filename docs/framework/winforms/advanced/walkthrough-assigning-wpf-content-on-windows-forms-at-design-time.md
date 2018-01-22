---
title: "Instruções passo a passo: atribuindo conteúdo WPF em Windows Forms na hora do design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93ff6f39f4d8bcdd037d373f8bd26cbb3c32c125
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a>Instruções passo a passo: atribuindo conteúdo WPF em Windows Forms na hora do design
Essa instrução passo a passo mostra como selecionar os tipos de controle do WPF (Windows Presentation Foundation) que você deseja exibir em seu formulário. Você pode selecionar qualquer tipo de controle WPF incluído no seu projeto.  
  
 Nesta instrução passo a passo, as seguintes tarefas serão executadas:  
  
-   Crie o projeto.  
  
-   Crie os tipos de controle WPF.  
  
-   Selecione os controles de WPF.  
  
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
  
-   Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `SelectingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>Criando tipos de controle WPF  
 Depois de adicionar tipos de controle WPF ao projeto, você pode hospedá-los em diferentes <xref:System.Windows.Forms.Integration.ElementHost> controles.  
  
#### <a name="to-create-wpf-control-types"></a>Criar tipos de controle WPF  
  
1.  Adicione um novo WPF <xref:System.Windows.Controls.UserControl> projeto à solução. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  No modo de exibição de Design, verifique se `UserControl1` está selecionado. Para obter mais informações, consulte [Como Selecionar e Mover Elementos na Superfície de Design](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades `200`.  
  
4.  Adicionar um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **conteúdo hospedado**.  
  
5.  Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao projeto. Use o nome padrão do tipo de controle, `UserControl2.xaml`.  
  
6.  No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades `200`.  
  
7.  Adicionar um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **2 conteúdo hospedado**.  
  
 **Observação** Em geral, é recomendável hospedar conteúdos WPF mais sofisticados. O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.  
  
1.  Compile o projeto.  
  
## <a name="selecting-wpf-controls"></a>Selecionando controles de WPF  
 Você pode atribuir diferente conteúdo WPF a um <xref:System.Windows.Forms.Integration.ElementHost> controle, que já está hospedando o conteúdo.  
  
#### <a name="to-select-wpf-controls"></a>Selecionar controles de WPF  
  
1.  Abra `Form1` no Designer de Formulários do Windows.  
  
2.  Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.  
  
     Uma instância de `UserControl1` está hospedada em um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.  
  
3.  No painel de smart tag para `elementHost1`, abra a lista suspensa **Selecionar conteúdo hospedado**.  
  
4.  Selecione **UserControl2** na caixa de listagem suspensa.  
  
     O controle `elementHost1` agora hospeda uma instância do tipo `UserControl2`.  
  
5.  No **propriedades** janela, confirme se o <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> está definida como **UserControl2**.  
  
6.  Do **caixa de ferramentas**, no **WPF Interoperability** de grupo, arraste um <xref:System.Windows.Forms.Integration.ElementHost> controle para o formulário.  
  
     O nome padrão do novo controle é `elementHost2`.  
  
7.  No painel de smart tag para `elementHost2`, abra a lista suspensa **Selecionar conteúdo hospedado**.  
  
8.  Selecione **UserControl1** na lista suspensa.  
  
9. O controle `elementHost2` agora hospeda uma instância do tipo `UserControl1`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migração e interoperabilidade](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Usando Controles do WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Designer do WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
