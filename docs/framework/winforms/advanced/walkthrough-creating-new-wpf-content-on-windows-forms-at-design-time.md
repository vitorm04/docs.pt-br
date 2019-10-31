---
title: 'Instruções passo a passo: criando novo conteúdo WPF em Windows Forms na hora do design'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fc6f988d6ffd270eba4abe277ca34fa2eeec56fd
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197429"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>Walkthrough: criar novo conteúdo do WPF em Windows Forms em tempo de design

Este artigo mostra como criar um controle Windows Presentation Foundation (WPF) para uso em seus aplicativos baseados em Windows Forms.

## <a name="prerequisites"></a>Prerequisites

É necessário o Visual Studio para concluir este passo a passo.

## <a name="create-the-project"></a>Criar o projeto

Abra o Visual Studio e crie um novo projeto de **aplicativo de Windows Forms (.NET Framework)** em C# Visual Basic ou Visual chamado `HostingWpf`.

> [!NOTE]
> Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.

## <a name="create-a-new-wpf-control"></a>Criar um novo controle WPF

Criar um novo controle WPF e adicioná-lo ao projeto é tão fácil quanto adicionar qualquer outro item ao projeto. O Designer de Formulários do Windows funciona com um determinado tipo de controle, chamado *controle de composição* ou *controle de usuário*. Para obter mais informações sobre controles de usuário do WPF, consulte <xref:System.Windows.Controls.UserControl>.

> [!NOTE]
> O tipo de <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> para WPF é diferente do tipo de controle de usuário fornecido pelo Windows Forms, que também é chamado de <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.

Para criar um novo controle WPF:

1. No **Gerenciador de soluções**, adicione um novo projeto de **.NET Framework (biblioteca de controle de usuário) do WPF** à solução. Use o nome padrão da biblioteca de controle, `WpfControlLibrary1`. O nome de controle padrão é `UserControl1.xaml`.

   Adicionar o novo controle tem os seguintes efeitos:

   - O arquivo UserControl1.xaml será adicionado.

   - O arquivo UserControl1.xaml.cs (ou UserControl1. XAML. vb) é adicionado. Este arquivo contém o code-behind para manipuladores de eventos e outras implementações.

   - Referências a assemblies WPF serão adicionadas.

   - O arquivo UserControl1. XAML é aberto no designer do WPF para Visual Studio.

2. No modo de exibição de Design, verifique se `UserControl1` está selecionado.

3. Na janela **Propriedades** , defina o valor das propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.

4. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> para a superfície de design.

5. Na janela **Propriedades** , defina o valor da propriedade <xref:System.Windows.Controls.TextBox.Text%2A> como **conteúdo hospedado**.

   > [!NOTE]
   > No geral, é necessário hospedar conteúdos do WPF mais sofisticados. O controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> é usado aqui apenas para fins ilustrativos.

6. Compile o projeto.

## <a name="add-a-wpf-control-to-a-windows-form"></a>Adicionar um controle WPF a um formulário do Windows

O novo controle WPF está pronto para uso no formulário. Windows Forms usa o controle <xref:System.Windows.Forms.Integration.ElementHost> para hospedar o conteúdo do WPF.

Para adicionar um controle WPF a um formulário do Windows:

1. Abra `Form1` no Designer de Formulários do Windows.

2. Na **Caixa de Ferramentas**, localize a guia com o rótulo **Controles de Usuário WPF WPFUserControlLibrary**.

3. Arraste uma instância de `UserControl1` para o formulário.

    - Um controle de <xref:System.Windows.Forms.Integration.ElementHost> é criado automaticamente no formulário para hospedar o controle WPF.

    - O controle <xref:System.Windows.Forms.Integration.ElementHost> é denominado `elementHost1` e, na janela **Propriedades** , você pode ver que sua propriedade <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> está definida como **UserControl1**.

    - Referências a assemblies WPF serão adicionadas ao projeto.

    - O controle `elementHost1` tem um painel de smart tag que mostra as opções de hospedagem disponíveis.

4. No painel de smart tag **ElementHost Tasks**, selecione **Encaixar no Contêiner Pai**.

5. Pressione **F5** para compilar e executar o aplicativo.

## <a name="next-steps"></a>Próximas etapas

O Windows Forms e o WPF são tecnologias diferentes, mas são projetados para interoperar estreitamente. Para fornecer aparência e comportamento mais ricos em seus aplicativos, tente o seguinte:

- Hospedar um controle dos Windows Forms em uma página WPF. Para obter mais informações, consulte [Instruções Passo a Passo: Hospedando um Controle dos Windows Forms no WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).

- Aplique estilos visuais dos Windows Forms ao conteúdo do WPF. Para obter mais informações, consulte [Como Habilitar Estilos Visuais em um Aplicativo Híbrido](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).

- Altere o estilo do conteúdo do WPF. Para obter mais informações, consulte [Instruções Passo a Passo: Definindo o Estilo do Conteúdo do WPF](walkthrough-styling-wpf-content.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migração e Interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar o XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
