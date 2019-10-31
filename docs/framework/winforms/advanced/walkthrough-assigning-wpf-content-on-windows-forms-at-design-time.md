---
title: 'Instruções passo a passo: atribuindo conteúdo WPF em Windows Forms na hora do design'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0fc7cf40acb141d698f59a1b7fbe6c32269ea61d
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197442"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>Walkthrough: atribuir conteúdo do WPF em Windows Forms em tempo de design

Este artigo mostra como selecionar os tipos de controle Windows Presentation Foundation (WPF) que você deseja exibir no formulário. Você pode selecionar qualquer tipo de controle WPF incluído no seu projeto.

## <a name="prerequisites"></a>Prerequisites

É necessário o Visual Studio para concluir este passo a passo.

## <a name="create-the-project"></a>Criar o projeto

Abra o Visual Studio e crie um novo projeto de aplicativo Windows Forms em Visual Basic C# ou Visual chamado `SelectingWpfContent`.

> [!NOTE]
> Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.

## <a name="create-the-wpf-control-types"></a>Criar os tipos de controle do WPF

Depois de adicionar tipos de controle do WPF ao projeto, você pode hospedá-los em diferentes controles de <xref:System.Windows.Forms.Integration.ElementHost>.

1. Adicione um novo projeto <xref:System.Windows.Controls.UserControl> do WPF à solução. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. No modo de exibição de Design, verifique se `UserControl1` está selecionado.

3. Na janela **Propriedades** , defina o valor das propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.

4. Adicione um controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> à <xref:System.Windows.Controls.UserControl> e defina o valor da propriedade <xref:System.Windows.Controls.TextBox.Text%2A> como **conteúdo hospedado**.

5. Adicione um segundo <xref:System.Windows.Controls.UserControl> do WPF ao projeto. Use o nome padrão do tipo de controle, `UserControl2.xaml`.

6. Na janela **Propriedades** , defina o valor das propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.

7. Adicione um controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> à <xref:System.Windows.Controls.UserControl> e defina o valor da propriedade <xref:System.Windows.Controls.TextBox.Text%2A> como o **conteúdo hospedado 2**.

   > [!NOTE]
   > No geral, é necessário hospedar conteúdos do WPF mais sofisticados. O controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> é usado aqui apenas para fins ilustrativos.

8. Compile o projeto.

## <a name="select-wpf-controls"></a>Selecionar controles WPF

Você pode atribuir conteúdo diferente do WPF a um controle <xref:System.Windows.Forms.Integration.ElementHost>, que já está hospedando o conteúdo.

1. Abra `Form1` no Designer de Formulários do Windows.

2. Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.

   Uma instância de `UserControl1` é hospedada em um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost1`.

3. No painel de smart tag para `elementHost1`, abra a lista suspensa **Selecionar conteúdo hospedado**.

4. Selecione **UserControl2** na caixa de listagem suspensa.

   O controle `elementHost1` agora hospeda uma instância do tipo `UserControl2`.

5. Na janela **Propriedades** , confirme se a propriedade <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> está definida como **UserControl2**.

6. Na **caixa de ferramentas**, no grupo de **interoperabilidade do WPF** , arraste um controle de <xref:System.Windows.Forms.Integration.ElementHost> para o formulário.

   O nome padrão do novo controle é `elementHost2`.

7. No painel de smart tag para `elementHost2`, abra a lista suspensa **Selecionar conteúdo hospedado**.

8. Selecione **UserControl1** na lista suspensa.

9. O controle `elementHost2` agora hospeda uma instância do tipo `UserControl1`.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migração e Interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar o XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
