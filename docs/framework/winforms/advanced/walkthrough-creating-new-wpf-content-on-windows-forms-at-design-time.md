---
title: 'Passo a passo: criar novo conteúdo WPF no Windows Forms na hora do design'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 889e81053d4e2264755468446a4e1681216ae22e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040370"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>Passo a passo: Criar novo conteúdo do WPF em Windows Forms em tempo de design

Este artigo mostra como criar um controle Windows Presentation Foundation (WPF) para uso em seus aplicativos baseados em Windows Forms.

Nesta instrução passo a passo, as seguintes tarefas serão executadas:

- Crie o projeto.

- Criar um novo controle WPF.

- Adicionar o novo controle WPF a um formulário do Windows Form. O controle WPF é hospedado em um <xref:System.Windows.Forms.Integration.ElementHost> controle.

## <a name="prerequisites"></a>Pré-requisitos

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Visual Studio

## <a name="create-the-project"></a>Criar o projeto

A primeira etapa é criar o projeto dos Windows Forms. Abra o Visual Studio e crie um novo projeto de **aplicativo de Windows Forms (.NET Framework)** em C# Visual Basic `HostingWpf`ou Visual chamado.

> [!NOTE]
> Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.

## <a name="create-a-new-wpf-control"></a>Criar um novo controle WPF

Criar um novo controle WPF e adicioná-lo ao projeto é tão fácil quanto adicionar qualquer outro item ao projeto. O Designer de Formulários do Windows funciona com um determinado tipo de controle, chamado *controle de composição* ou *controle de usuário*. Para obter mais informações sobre controles de usuário do <xref:System.Windows.Controls.UserControl>WPF, consulte.

> [!NOTE]
> O <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> tipo de WPF é diferente do tipo de controle de usuário fornecido pelo Windows Forms, que também é <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>chamado de.

Para criar um novo controle WPF:

1. No **Gerenciador de soluções**, adicione um novo projeto de **.NET Framework (biblioteca de controle de usuário) do WPF** à solução. Use o nome padrão da biblioteca de controle, `WpfControlLibrary1`. O nome de controle padrão é `UserControl1.xaml`.

     Adicionar o novo controle tem os seguintes efeitos:

    - O arquivo UserControl1.xaml será adicionado.

    - O arquivo UserControl1.xaml.cs ou UserControl1.xaml.vb será adicionado. Este arquivo contém o code-behind para manipuladores de eventos e outras implementações.

    - Referências a assemblies WPF serão adicionadas.

    - O arquivo UserControl1.xaml será aberto no [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].

2. No modo de exibição de Design, verifique se `UserControl1` está selecionado. Para obter mais informações, confira [Como: Selecione e mova elementos no Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).

3. Na janela **Propriedades** , defina o valor das <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.

4. Na **caixa de ferramentas**, arraste <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> um controle para a superfície de design.

5. Na janela **Propriedades** , defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> Propriedade como **conteúdo hospedado**.

    > [!NOTE]
    > No geral, é necessário hospedar conteúdos do WPF mais sofisticados. O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.

6. Compile o projeto.

## <a name="add-a-wpf-control-to-a-windows-form"></a>Adicionar um controle WPF a um formulário do Windows

O novo controle WPF está pronto para uso no formulário. Windows Forms usa o <xref:System.Windows.Forms.Integration.ElementHost> controle para hospedar o conteúdo do WPF.

Para adicionar um controle WPF a um formulário do Windows:

1. Abra `Form1` no Designer de Formulários do Windows.

2. Na **Caixa de Ferramentas**, localize a guia com o rótulo **Controles de Usuário WPF WPFUserControlLibrary**.

3. Arraste uma instância de `UserControl1` para o formulário.

    - Um <xref:System.Windows.Forms.Integration.ElementHost> controle é criado automaticamente no formulário para hospedar o controle WPF.

    - O <xref:System.Windows.Forms.Integration.ElementHost> controle é nomeado `elementHost1` e na janela **Propriedades** , você pode ver que sua <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> Propriedade está definida como **UserControl1**.

    - Referências a assemblies WPF serão adicionadas ao projeto.

    - O controle `elementHost1` tem um painel de smart tag que mostra as opções de hospedagem disponíveis.

4. No painel de smart tag **ElementHost Tasks**, selecione **Encaixar no Contêiner Pai**.

5. Pressione **F5** para compilar e executar o aplicativo.

## <a name="next-steps"></a>Próximas etapas

O Windows Forms e o WPF são tecnologias diferentes, mas são projetados para interoperar estreitamente. Para fornecer aparência e comportamento mais ricos em seus aplicativos, tente o seguinte:

- Hospedar um controle dos Windows Forms em uma página WPF. Para obter mais informações, confira [Passo a passo: Hospedagem de um controle de Windows Forms](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)no WPF.

- Aplique estilos visuais dos Windows Forms ao conteúdo do WPF. Para obter mais informações, confira [Como: Habilitar estilos visuais em um aplicativo](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)híbrido.

- Altere o estilo do conteúdo do WPF. Para obter mais informações, confira [Passo a passo: Estilizando conteúdo](walkthrough-styling-wpf-content.md)do WPF.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migração e interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
