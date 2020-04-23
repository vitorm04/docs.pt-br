---
title: Crie um estilo para um controle
description: Aprenda a criar e referenciar um estilo de controle no Windows Presentation Foundation e no .NET Core.
author: thraka
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2956dbf93a1d34feca31d3ab10536f5089010189
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "82071265"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>Crie um estilo para um controle no WPF

Com o Windows Presentation Foundation (WPF), você pode personalizar a aparência de um controle existente com seu próprio estilo reutilizável. Os estilos podem ser aplicados globalmente ao seu aplicativo, janelas e páginas, ou diretamente aos controles.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Criar um estilo

Você pode pensar <xref:System.Windows.Style> em uma maneira conveniente de aplicar um conjunto de valores de propriedade a um ou mais elementos. Você pode usar um estilo em <xref:System.Windows.FrameworkElement> qualquer <xref:System.Windows.FrameworkContentElement> elemento <xref:System.Windows.Window> que <xref:System.Windows.Controls.Button>deriva ou como um ou um .

A maneira mais comum de declarar um `Resources` estilo é como um recurso na seção em um arquivo XAML. Como estilos são recursos, eles obedecem às mesmas regras de escopo que se aplicam a todos os recursos. Simplificando, onde você declara que um estilo afeta onde o estilo pode ser aplicado. Por exemplo, se você declarar o estilo no elemento raiz do arquivo XAML da definição do aplicativo, o estilo pode ser usado em qualquer lugar do seu aplicativo.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Se você declarar o estilo em um dos arquivos XAML do aplicativo, o estilo só pode ser usado nesse arquivo XAML. Para obter mais informações sobre regras de escopo para recursos, consulte [Recursos de XAML](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Um estilo é `<Setter>` composto de elementos infantis que definem propriedades nos elementos aos os que o estilo é aplicado. No exemplo acima, observe que o estilo `TextBlock` é `TargetType` definido para aplicar a tipos através do atributo. O estilo <xref:System.Windows.Controls.Control.FontSize%2A> definirá `15` o <xref:System.Windows.Controls.Control.FontWeight%2A> `ExtraBold`to e o to . Adicione `<Setter>` a para cada propriedade as mudanças de estilo.

## <a name="apply-a-style-implicitly"></a>Aplique um estilo implicitamente

A <xref:System.Windows.Style> é uma maneira conveniente de aplicar um conjunto de valores de propriedade a mais de um elemento. Por exemplo, considere <xref:System.Windows.Controls.TextBlock> os seguintes elementos e sua aparência padrão em uma janela.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Captura de tela de amostra de estilo](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Você pode alterar a aparência padrão <xref:System.Windows.Controls.Control.FontSize%2A> definindo propriedades, como e <xref:System.Windows.Controls.Control.FontFamily%2A>, em cada <xref:System.Windows.Controls.TextBlock> elemento diretamente. No entanto, <xref:System.Windows.Controls.TextBlock> se você quiser que seus <xref:System.Windows.Style> elementos `Resources` compartilhem algumas propriedades, você pode criar um na seção do seu arquivo XAML, como mostrado aqui.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

Quando você <xref:System.Windows.Style.TargetType%2A> define o do <xref:System.Windows.Controls.TextBlock> seu estilo para `x:Key` o tipo e omite o atributo, o estilo é aplicado a todos os <xref:System.Windows.Controls.TextBlock> elementos escopo do estilo, que geralmente é o próprio arquivo XAML.

Agora <xref:System.Windows.Controls.TextBlock> os elementos aparecem da seguinte forma.

![Captura de tela de amostra de estilo](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Aplique um estilo explicitamente

Se você `x:Key` adicionar um atributo com valor ao estilo, o estilo <xref:System.Windows.Style.TargetType%2A>não será mais aplicado implicitamente a todos os elementos de . Apenas elementos que fazem referência explícita ao estilo terão o estilo aplicado a eles.

Aqui está o estilo da seção anterior, mas declarado com o atributo. `x:Key`

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Para aplicar o estilo, defina <xref:System.Windows.FrameworkElement.Style%2A> a `x:Key` propriedade no elemento para o valor, usando uma [extensão de marcação StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md), conforme mostrado aqui.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

Observe que <xref:System.Windows.Controls.TextBlock> o primeiro elemento tem o estilo aplicado a ele enquanto o segundo elemento TextBlock permanece inalterado. O estilo implícito da seção anterior foi `x:Key` alterado para um estilo que declarou o atributo, ou seja, o único elemento afetado pelo estilo é aquele que fazia referência diretamente ao estilo.

![Captura de tela de amostra de estilo](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "criar-um-estilo-explicitamente-textblock")

Uma vez que um estilo é aplicado, explicitamente ou implicitamente, ele se torna selado e não pode ser alterado. Se você quiser alterar um estilo que foi aplicado, crie um novo estilo para substituir o existente. Para obter mais informações, consulte a propriedade <xref:System.Windows.Style.IsSealed%2A>.

É possível criar um objeto que escolhe um estilo para aplicar com base na lógica personalizada. Por exemplo, veja o exemplo <xref:System.Windows.Controls.StyleSelector> fornecido para a classe.

## <a name="apply-a-style-programmatically"></a>Aplique um estilo programáticamente

Para atribuir um estilo nomeado a um elemento programáticamente, obtenha o estilo da <xref:System.Windows.FrameworkElement.Style%2A> coleção de recursos e atribua-o à propriedade do elemento. Os itens de uma coleção de <xref:System.Object>recursos são do tipo . Portanto, você deve lançar o estilo <xref:System.Windows.Style?displayProperty=fullName> recuperado para um `Style` antes de atribuí-lo à propriedade. Por exemplo, o código a `TextBlock` seguir `textblock1` define o `TitleText`estilo de um nome para o estilo definido .

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Estender um estilo

Talvez você queira <xref:System.Windows.Controls.TextBlock> que seus dois elementos <xref:System.Windows.Controls.Control.FontFamily%2A> compartilhem alguns valores de propriedade, como o e o centrado. <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Mas você também quer que o texto **Minhas Fotos** tenha algumas propriedades adicionais. Você pode fazer isso criando um novo estilo que é baseado no primeiro estilo, como mostrado aqui.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Este `TextBlock` estilo agora está centrado, usa `Comic Sans MS` uma `26`fonte com um tamanho de <xref:System.Windows.Media.LinearGradientBrush> , e a cor de primeiro plano definida para o mostrado no exemplo. Observe que ele <xref:System.Windows.Controls.Control.FontSize%2A> substitui o valor do estilo base. Se há mais de <xref:System.Windows.Setter> um apontando para <xref:System.Windows.Style>a `Setter` mesma propriedade em um , o que é declarado por último tem precedência.

O seguinte mostra <xref:System.Windows.Controls.TextBlock> como os elementos agora se parecem:

![Blocos de texto estilizados](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Este `TitleText` estilo estende o estilo que <xref:System.Windows.Controls.TextBlock> foi criado para `BasedOn="{StaticResource {x:Type TextBlock}}"`o tipo, referenciado com . Você também pode estender um `x:Key` estilo `x:Key` que tem um usando o do estilo. Por exemplo, se houvesse `Header1` um estilo chamado e você quisesse `BasedOn="{StaticResource Header1}"`estender esse estilo, você usaria .

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relacionamento da propriedade TargetType e do atributo x:Key

Como mostrado anteriormente, <xref:System.Windows.Style.TargetType%2A> definir `TextBlock` a propriedade sem atribuir o estilo `x:Key` faz <xref:System.Windows.Controls.TextBlock> com que o estilo seja aplicado a todos os elementos. Nesse caso, o `x:Key` é definido implicitamente como `{x:Type TextBlock}`. Isso significa que, se `x:Key` você definir explicitamente `{x:Type TextBlock}`o <xref:System.Windows.Style> valor para qualquer `TextBlock` outra coisa que não, o não é aplicado a todos os elementos automaticamente. Em vez disso, você deve `x:Key` aplicar o `TextBlock` estilo (usando o valor) aos elementos explicitamente. Se o seu estilo estiver na seção `TargetType` de recursos e você não `x:Key` definir a propriedade no seu estilo, então você deve definir o atributo.

Além de fornecer um valor `x:Key`padrão `TargetType` para o , a propriedade especifica o tipo a que as propriedades do setter se aplicam. Se você não especificar um `TargetType`, você <xref:System.Windows.Setter> deve qualificar as propriedades em seus `Property="ClassName.Property"`objetos com um nome de classe usando a sintaxe . Por exemplo, em `Property="FontSize"`vez de <xref:System.Windows.Setter.Property%2A> `"TextBlock.FontSize"` definir, você deve definir ou `"Control.FontSize"`.

Observe também que muitos controles WPF consistem em uma combinação de outros controles WPF. Caso você crie um estilo que se aplica a todos os controles de um tipo, pode obter resultados inesperados. Por exemplo, se você criar um <xref:System.Windows.Controls.TextBlock> estilo <xref:System.Windows.Window>que visa o tipo `TextBlock` em a, o estilo `TextBlock` é aplicado a todos os <xref:System.Windows.Controls.ListBox>controles na janela, mesmo que o seja parte de outro controle, como um .

## <a name="see-also"></a>Confira também

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [Visão geral dos recursos XAML](xaml-resources-define.md)
- [Visão geral xaml (WPF & .NET Core)](xaml.md)
