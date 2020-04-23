---
title: Crie um modelo no WPF - .NET Desktop
description: Aprenda a criar e referenciar um modelo de controle no Windows Presentation Foundation e no .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071244"
---
# <a name="create-a-template-for-a-control"></a>Crie um modelo para um controle

Com o Windows Presentation Foundation (WPF), você pode personalizar a estrutura visual e o comportamento de um controle existente com seu próprio modelo reutilizável. Os modelos podem ser aplicados globalmente ao seu aplicativo, janelas e páginas ou diretamente aos controles. A maioria dos cenários que exigem que você crie um novo controle pode ser coberto criando um novo modelo para um controle existente.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Neste artigo, você explorará a <xref:System.Windows.Controls.ControlTemplate> criação <xref:System.Windows.Controls.Button> de um novo para o controle.

## <a name="when-to-create-a-controltemplate"></a>Quando criar um ControlTemplate

Os controles têm muitas <xref:System.Windows.Controls.Border.Background%2A>propriedades, tais como, <xref:System.Windows.Controls.Control.Foreground%2A>e <xref:System.Windows.Controls.Control.FontFamily%2A>. Essas propriedades controlam diferentes aspectos da aparência do controle, mas as alterações que você pode fazer definindo essas propriedades são limitadas. Por exemplo, você <xref:System.Windows.Controls.Control.Foreground%2A> pode definir <xref:System.Windows.Controls.Control.FontStyle%2A> a propriedade como <xref:System.Windows.Controls.CheckBox>azul e itálica em um . Quando você deseja personalizar a aparência do controle além do que a configuração das outras propriedades no controle pode fazer, você cria um <xref:System.Windows.Controls.ControlTemplate>.

Na maioria das interfaces de usuário, um botão tem a mesma aparência geral: um retângulo com algum texto. Se você quiser criar um botão arredondado, você pode criar um novo controle que herda do botão ou recria a funcionalidade do botão. Além disso, o novo controle do usuário forneceria o visual circular.

Você pode evitar criar novos controles personalizando o layout visual de um controle existente. Com um botão arredondado, você cria um <xref:System.Windows.Controls.ControlTemplate> com o layout visual desejado.

Por outro lado, se você precisar de um controle com novas funcionalidades, diferentes propriedades e novas configurações, você criará um novo <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Pré-requisitos

Crie um novo aplicativo WPF e no *MainWindow.xaml* (ou outra janela ** \<** de sua escolha) defina as seguintes propriedades no elemento Janela>:

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

Defina o conteúdo do elemento ** \<Janela>** para o seguinte XAML:

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

No final, o arquivo *MainWindow.xaml* deve ser semelhante ao seguinte:

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

Se você executar o aplicativo, ele se parece com o seguinte:

![Janela WPF com dois botões sem estilo](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>Criar um ControlTemplate

A maneira mais comum de declarar <xref:System.Windows.Controls.ControlTemplate> `Resources` a é como um recurso na seção em um arquivo XAML. Como os modelos são recursos, eles obedecem às mesmas regras de escopo que se aplicam a todos os recursos. Simplificando, onde você declara que um modelo afeta onde o modelo pode ser aplicado. Por exemplo, se você declarar o modelo no elemento raiz do arquivo XAML da definição do aplicativo, o modelo poderá ser usado em qualquer lugar do seu aplicativo. Se você definir o modelo em uma janela, apenas os controles dessa janela podem usar o modelo.

Para começar, adicione `Window.Resources` um elemento ao seu arquivo *MainWindow.xaml:*

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

Crie um novo ** \<>ControlTemplate** com o seguinte conjunto de propriedades:

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

Este modelo de controle será simples:

- um elemento raiz para o controle, um<xref:System.Windows.Controls.Grid>
- um <xref:System.Windows.Shapes.Ellipse> para desenhar a aparência arredondada do botão
- a <xref:System.Windows.Controls.ContentPresenter> para exibir o conteúdo do botão especificado pelo usuário

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

Quando você cria <xref:System.Windows.Controls.ControlTemplate>um novo , você ainda pode querer usar as propriedades públicas para alterar a aparência do controle. A extensão [de marcação De vinculação de modelos](../../framework/wpf/advanced/templatebinding-markup-extension.md) vincula uma propriedade de um elemento que está no <xref:System.Windows.Controls.ControlTemplate> a um imóvel público definido pelo controle. Quando você usa um [TemplateBinding,](../../framework/wpf/advanced/templatebinding-markup-extension.md)você habilita propriedades no controle para agir como parâmetros para o modelo. Ou seja, quando uma propriedade em um controle é definida, esse valor é passado para o elemento que contém a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md).

### <a name="ellipse"></a>Ellipse

Observe que **:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** as propriedades do elemento ** \<Ellipse>** estão <xref:System.Windows.Controls.Control.Foreground> <xref:System.Windows.Controls.Control.Background> ligadas ao controle e propriedades.

### <a name="contentpresenter"></a>ContentPresenter

Um elemento [ \<de>de ContentPresenter](xref:System.Windows.Controls.ContentPresenter) também é adicionado ao modelo. Como este modelo foi projetado para um botão, leve <xref:System.Windows.Controls.ContentControl>em consideração que o botão herda de . O botão apresenta o conteúdo do elemento. Você pode definir qualquer coisa dentro do botão, como texto simples ou até mesmo outro controle. Ambos os botões a seguir são válidos:

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

Em ambos os exemplos anteriores, o texto e a caixa de seleção são definidos como a propriedade [Button.Content.](xref:System.Windows.Controls.ContentControl.Content) O que for definido como o conteúdo pode ser apresentado através de um ** \<contentPresenter>**, que é o que o modelo faz.

Se <xref:System.Windows.Controls.ControlTemplate> o é aplicado <xref:System.Windows.Controls.ContentControl> a um `Button`tipo, <xref:System.Windows.Controls.ContentPresenter> como a , a é pesquisado na árvore de elementos. Se `ContentPresenter` for encontrado, o modelo vincula automaticamente <xref:System.Windows.Controls.ContentControl.Content> a `ContentPresenter`propriedade do controle ao .

## <a name="use-the-template"></a>Usar o modelo

Encontre os botões que foram declarados no início deste artigo.

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Defina a propriedade <xref:System.Windows.Controls.Control.Template> do `roundbutton` segundo botão para o recurso:

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

Se você executar o projeto e olhar para o resultado, você verá que o botão tem um fundo arredondado.

![Janela WPF com um botão oval de modelo](media/create-apply-template/styled-button.png)

Você deve ter notado que o botão não é um círculo, mas está distorcido. Devido à forma ** \<** como o elemento Elipse>funciona, ele sempre se expande para preencher o espaço disponível. Faça o uniforme do círculo **:::no-loc text="width":::** alterando o botão e **:::no-loc text="height":::** as propriedades para o mesmo valor:

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Janela WPF com um botão circular de modelo](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>Adicionar um gatilho

Mesmo que um botão com um modelo aplicado pareça diferente, ele se comporta da mesma forma que qualquer outro botão. Se você apertar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> botão, o evento é acionado. No entanto, você deve ter notado que quando você move o mouse sobre o botão, o visual do botão não muda. Essas interações visuais são todas definidas pelo modelo.

Com os sistemas dinâmicos de eventos e propriedades que o WPF fornece, você pode observar uma propriedade específica por um valor e, em seguida, reestilizar o modelo quando apropriado. Neste exemplo, você observará a <xref:System.Windows.UIElement.IsMouseOver> propriedade do botão. Quando o mouse estiver sobre o controle, estilize o ** \<>de Elipse** com uma nova cor. Este tipo de gatilho é conhecido como *PropertyTrigger*.

Para que isso funcione, você precisará adicionar um nome ao ** \<>de Elipse** que você pode referenciar. Dê-lhe o nome de **backgroundElement**.

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

Em seguida, <xref:System.Windows.Trigger> adicione um novo à coleção [ControlTemplate.Triggers.](xref:System.Windows.Controls.ControlTemplate.Triggers) O gatilho observará o `IsMouseOver` `true`evento pelo valor.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

Em seguida, adicione um ** \<setter>** ao ** \<trigger>** que altera a propriedade **Preenchimento** do ** \<>de Elipse** para uma nova cor.

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

Execute o projeto. Observe que quando você move o mouse sobre o botão, a cor da ** \<elipse>** muda.

![mouse move sobre o botão WPF para alterar a cor de preenchimento](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>Use um VisualState

Os estados visuais são definidos e acionados por um controle. Por exemplo, quando o mouse é movido `CommonStates.MouseOver` em cima do controle, o estado é acionado. Você pode animar as mudanças de propriedade com base no estado atual do controle. Na seção anterior, `IsMouseOver` um `true` ** \<>PropertyTrigger** foi usado para `AliceBlue` alterar o primeiro plano do botão para quando a propriedade era . Em vez disso, crie um estado visual que anima a mudança dessa cor, proporcionando uma transição suave. Para obter mais informações sobre *o VisualStates,* consulte [Estilos e modelos no WPF](../fundamentals/styles-templates-overview.md#visual-states).

Para converter ** \<oTrigger>em** um estado visual animado, primeiro, remova o ** \<elemento ControlTemplate.Triggers>** do seu modelo.

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

Em seguida, ** \<** na grade>raiz do modelo de controle, adicione o `CommonStates` ** \<elemento visualStateManager.VisualStateGroups>** com um ** \<visualStateGroup>** para . Defina dois `Normal` `MouseOver`estados, e .

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

Todas as animações definidas em um ** \<visualState>** são aplicadas quando esse estado é acionado. Crie animações para cada estado. As animações são ** \<** colocadas dentro de um elemento de>storyboard. Para obter mais informações sobre storyboards, consulte [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

- Normal

  Este estado anima o preenchimento de elipse, restaurando-o à cor do `Background` controle.

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- MouseOver

  Este estado anima a `Background` cor da elipse `Yellow`a uma nova cor: .

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

O ** \<>ControlTemplate** deve agora parecer o seguinte.

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

Execute o projeto. Observe que quando você move o mouse sobre o botão, a cor da ** \<elipse>** anima.

![mouse move sobre o botão WPF para alterar a cor de preenchimento](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>Próximas etapas

- [Crie um estilo para um controle no WPF](../fundamentals/styles-templates-create-apply-style.md)
- [Estilos e modelos em WPF](../fundamentals/styles-templates-overview.md)
- [Visão geral dos recursos XAML](../fundamentals/xaml-resources-define.md)
