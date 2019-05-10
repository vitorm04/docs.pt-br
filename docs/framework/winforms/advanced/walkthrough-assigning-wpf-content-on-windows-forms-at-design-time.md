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
ms.openlocfilehash: 09427bfc836f40ca9c7aa76f4904bfe7083bf8dc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211231"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>Passo a passo: Atribuir o conteúdo do WPF nos Windows Forms em tempo de design

Essa instrução passo a passo mostra como selecionar os tipos de controle do WPF (Windows Presentation Foundation) que você deseja exibir em seu formulário. Você pode selecionar qualquer tipo de controle WPF incluído no seu projeto.

Nesta instrução passo a passo, as seguintes tarefas serão executadas:

- Crie o projeto.

- Crie os tipos de controle WPF.

- Selecione os controles de WPF.

## <a name="prerequisites"></a>Pré-requisitos

É necessário o Visual Studio para concluir este passo a passo.

## <a name="create-the-project"></a>Criar o projeto

Abra o Visual Studio e crie um novo projeto de aplicativo do Windows Forms no Visual Basic ou Visual C# nomeado `SelectingWpfContent`.

> [!NOTE]
> Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.

## <a name="create-the-wpf-control-types"></a>Criar os tipos de controle do WPF

Depois de adicionar tipos de controle WPF ao projeto, você pode hospedá-los em diferentes <xref:System.Windows.Forms.Integration.ElementHost> controles.

## <a name="create-wpf-control-types"></a>Criar tipos de controle WPF

1. Adicione um novo WPF <xref:System.Windows.Controls.UserControl> projeto à solução. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, confira [Passo a passo: Criando novo conteúdo WPF nos Windows Forms em tempo de Design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. No modo de exibição de Design, verifique se `UserControl1` está selecionado. Para obter mais informações, confira [Como: Selecionar e mover elementos na superfície de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).

3. No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades a serem `200`.

4. Adicionar um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **conteúdo hospedado**.

5. Adicione um segundo WPF <xref:System.Windows.Controls.UserControl> ao projeto. Use o nome padrão do tipo de controle, `UserControl2.xaml`.

6. No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades a serem `200`.

7. Adicionar um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **conteúdo hospedado 2**.

 **Observação** Em geral, é recomendável hospedar conteúdos WPF mais sofisticados. O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.

1. Compile o projeto.

## <a name="select-wpf-controls"></a>Selecione controles WPF

Você pode atribuir diferentes conteúdos WPF a um <xref:System.Windows.Forms.Integration.ElementHost> controle, que já está hospedando o conteúdo.

1. Abra `Form1` no Designer de Formulários do Windows.

2. Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.

     Uma instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.

3. No painel de smart tag para `elementHost1`, abra a lista suspensa **Selecionar conteúdo hospedado**.

4. Selecione **UserControl2** na caixa de listagem suspensa.

     O controle `elementHost1` agora hospeda uma instância do tipo `UserControl2`.

5. No **propriedades** janela, confirme se o <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> estiver definida como **UserControl2**.

6. Dos **caixa de ferramentas**, no **interoperabilidade do WPF** de grupo, arraste um <xref:System.Windows.Forms.Integration.ElementHost> controle para o formulário.

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
