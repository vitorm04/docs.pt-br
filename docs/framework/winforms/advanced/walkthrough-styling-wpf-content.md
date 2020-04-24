---
title: 'Passo a passo: Conteúdo do Estilo WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07241d41e3fbf270a76bd241765bfa369ee265d5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646324"
---
# <a name="walkthrough-style-wpf-content"></a>Passo a passo: Conteúdo do Estilo WPF

Este artigo mostra como aplicar o estilo a um controle do Windows Presentation Foundation (WPF) hospedado em um formulário do Windows.

## <a name="prerequisites"></a>Pré-requisitos

É necessário o Visual Studio para concluir este passo a passo.

## <a name="create-the-project"></a>Criar o projeto

Abra o Visual Studio e crie um novo projeto de `StylingWpfContent`aplicativo de formulários do Windows em visual básico ou visual C# chamado .

> [!NOTE]
> Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.

## <a name="create-the-wpf-control-types"></a>Crie os tipos de controle WPF

Depois de adicionar um tipo de controle WPF ao <xref:System.Windows.Forms.Integration.ElementHost> projeto, você pode hospedá-lo em um controle.

1. Adicione um novo <xref:System.Windows.Controls.UserControl> projeto WPF à solução. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. No modo de exibição de Design, verifique se `UserControl1` está selecionado.

3. Na janela **Propriedades,** defina <xref:System.Windows.FrameworkElement.Width%2A> o <xref:System.Windows.FrameworkElement.Height%2A> valor das propriedades e das propriedades para **200**.

4. Adicione <xref:System.Windows.Controls.Button?displayProperty=nameWithType> um controle <xref:System.Windows.Controls.UserControl> ao e defina o <xref:System.Windows.Controls.ContentControl.Content%2A> valor da propriedade como **Cancel**.

5. Adicione um <xref:System.Windows.Controls.Button?displayProperty=nameWithType> segundo <xref:System.Windows.Controls.UserControl> controle ao e <xref:System.Windows.Controls.ContentControl.Content%2A> defina o valor da propriedade como **OK**.

6. Compile o projeto.

## <a name="apply-a-style-to-a-wpf-control"></a>Aplique um estilo a um controle WPF

Você pode aplicar um estilo diferente a um controle WPF para alterar sua aparência e comportamento.

1. Abra `Form1` no Designer de Formulários do Windows.

1. Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.

   Um exemplo `UserControl1` de está hospedado <xref:System.Windows.Forms.Integration.ElementHost> em `elementHost1`um novo controle chamado .

1. No painel de smart tag para `elementHost1`, clique em **Editar conteúdo hospedado** na lista suspensa.

   `UserControl1`abre no WPF Designer.

1. Na exibição XAML, insira o seguinte XAML após a marca de abertura `<UserControl>`. Esse XAML cria um gradiente com uma borda gradiente de contraste. Ao clicar no controle, os gradientes são alterados para gerar uma aparência de botão pressionado. Para obter mais informações, consulte [Styling e Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

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

1. Aplique `SimpleButton` o estilo definido na etapa anterior ao botão Cancelar, inserindo o Seguinte XAML na `<Button>` marca do botão **Cancelar.**

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Sua declaração de botão se assemelhará ao seguinte XAML:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Compile o projeto.

1. Abra `Form1` no Designer de Formulários do Windows.

1. O novo estilo é aplicado ao controle de botão.

1. No menu **Depuração**, selecione **Iniciar Depuração** para executar o aplicativo.

1. Clique nos botões **OK** e **Cancel** e veja as diferenças.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migração e interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
