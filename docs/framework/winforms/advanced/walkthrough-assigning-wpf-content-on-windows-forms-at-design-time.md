---
title: 'Passo a passo: atribuir conteúdo WPF no Windows Forms na hora do design'
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
ms.openlocfilehash: bc5f5e2d8808c0a60df721bf2c0ed76b45ef49a0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666256"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>Passo a passo: Atribuir conteúdo do WPF em Windows Forms em tempo de design

Este artigo mostra como selecionar os tipos de controle Windows Presentation Foundation (WPF) que você deseja exibir no formulário. Você pode selecionar qualquer tipo de controle WPF incluído no seu projeto.

## <a name="prerequisites"></a>Pré-requisitos

É necessário o Visual Studio para concluir este passo a passo.

## <a name="create-the-project"></a>Criar o projeto

Abra o Visual Studio e crie um novo projeto de aplicativo Windows Forms em Visual Basic C# ou `SelectingWpfContent`Visual chamado.

> [!NOTE]
> Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.

## <a name="create-the-wpf-control-types"></a>Criar os tipos de controle do WPF

Depois de adicionar tipos de controle do WPF ao projeto, você pode hospedá-los <xref:System.Windows.Forms.Integration.ElementHost> em controles diferentes.

1. Adicione um novo projeto <xref:System.Windows.Controls.UserControl> do WPF à solução. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, confira [Passo a passo: Criando novo conteúdo do WPF em Windows Forms em tempo](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de design.

2. No modo de exibição de Design, verifique se `UserControl1` está selecionado.

3. Na janela **Propriedades** , defina o valor das <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.

4. Adicione um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> <xref:System.Windows.Controls.UserControl> controle ao e <xref:System.Windows.Controls.TextBox.Text%2A> defina o valor da propriedade como **conteúdo hospedado**.

5. Adicione um segundo WPF <xref:System.Windows.Controls.UserControl> ao projeto. Use o nome padrão do tipo de controle, `UserControl2.xaml`.

6. Na janela **Propriedades** , defina o valor das <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.

7. Adicione um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> <xref:System.Windows.Controls.UserControl> controle ao e <xref:System.Windows.Controls.TextBox.Text%2A> defina o valor da propriedade como **conteúdo hospedado 2**.

   > [!NOTE]
   > No geral, é necessário hospedar conteúdos do WPF mais sofisticados. O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.

8. Compile o projeto.

## <a name="select-wpf-controls"></a>Selecionar controles WPF

Você pode atribuir conteúdo WPF diferente a um <xref:System.Windows.Forms.Integration.ElementHost> controle, que já está hospedando conteúdo.

1. Abra `Form1` no Designer de Formulários do Windows.

2. Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.

   Uma instância do `UserControl1` é hospedada em um <xref:System.Windows.Forms.Integration.ElementHost> novo controle `elementHost1`chamado.

3. No painel de smart tag para `elementHost1`, abra a lista suspensa **Selecionar conteúdo hospedado**.

4. Selecione **UserControl2** na caixa de listagem suspensa.

   O controle `elementHost1` agora hospeda uma instância do tipo `UserControl2`.

5. Na janela **Propriedades** , confirme se a <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> Propriedade está definida como **UserControl2**.

6. Na **caixa de ferramentas**, no grupo de interoperabilidade do **WPF** , arraste um <xref:System.Windows.Forms.Integration.ElementHost> controle para o formulário.

   O nome padrão do novo controle é `elementHost2`.

7. No painel de smart tag para `elementHost2`, abra a lista suspensa **Selecionar conteúdo hospedado**.

8. Selecione **UserControl1** na lista suspensa.

9. O controle `elementHost2` agora hospeda uma instância do tipo `UserControl1`.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migração e interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
