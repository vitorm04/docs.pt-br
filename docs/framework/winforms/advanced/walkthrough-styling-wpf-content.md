---
title: 'Instruções passo a passo: criando o conteúdo WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 581fcbfdfd7806b8f0f70347ac96f1bf09fa9098
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460939"
---
# <a name="walkthrough-style-wpf-content"></a>Walkthrough: estilo de conteúdo do WPF

Este artigo mostra como aplicar o estilo a um controle Windows Presentation Foundation (WPF) hospedado em um formulário do Windows.

## <a name="prerequisites"></a>Prerequisites

É necessário o Visual Studio para concluir este passo a passo.

## <a name="create-the-project"></a>Criar o projeto

Abra o Visual Studio e crie um novo projeto de aplicativo Windows Forms em Visual Basic C# ou Visual chamado `StylingWpfContent`.

> [!NOTE]
> Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.

## <a name="create-the-wpf-control-types"></a>Criar os tipos de controle do WPF

Depois de adicionar um tipo de controle do WPF ao projeto, você pode hospedá-lo em um controle de <xref:System.Windows.Forms.Integration.ElementHost>.

1. Adicione um novo projeto <xref:System.Windows.Controls.UserControl> do WPF à solução. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. No modo de exibição de Design, verifique se `UserControl1` está selecionado.

3. Na janela **Propriedades** , defina o valor das propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.

4. Adicione um controle de <xref:System.Windows.Controls.Button?displayProperty=nameWithType> à <xref:System.Windows.Controls.UserControl> e defina o valor da propriedade <xref:System.Windows.Controls.ContentControl.Content%2A> como **Cancelar**.

5. Adicione um segundo controle de <xref:System.Windows.Controls.Button?displayProperty=nameWithType> à <xref:System.Windows.Controls.UserControl> e defina o valor da propriedade <xref:System.Windows.Controls.ContentControl.Content%2A> como **OK**.

6. Compile o projeto.

## <a name="apply-a-style-to-a-wpf-control"></a>Aplicar um estilo a um controle WPF

Você pode aplicar um estilo diferente a um controle WPF para alterar sua aparência e comportamento.

1. Abra `Form1` no Designer de Formulários do Windows.

1. Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.

   Uma instância de `UserControl1` é hospedada em um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost1`.

1. No painel de smart tag para `elementHost1`, clique em **Editar conteúdo hospedado** na lista suspensa.

   o `UserControl1` é aberto no designer do WPF.

1. Na exibição XAML, insira o seguinte XAML após a marca de abertura `<UserControl>`. Esse XAML cria um gradiente com uma borda gradiente de contraste. Ao clicar no controle, os gradientes são alterados para gerar uma aparência de botão pressionado. Para obter mais informações, consulte [Estilo e modelagem](../../wpf/controls/styling-and-templating.md).

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

1. Aplique o estilo de `SimpleButton` definido na etapa anterior ao botão Cancelar inserindo o XAML a seguir na marca de `<Button>` do botão **Cancelar** .

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   A declaração do botão será semelhante ao seguinte XAML:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Compile o projeto.

1. Abra `Form1` no Designer de Formulários do Windows.

1. O novo estilo é aplicado ao controle de botão.

1. No menu **Depuração**, selecione **Iniciar Depuração** para executar o aplicativo.

1. Clique nos botões **OK** e **Cancelar** e exiba as diferenças.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migração e Interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar o XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Visão geral de XAML (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [Estilo e modelagem](../../wpf/controls/styling-and-templating.md)
