---
title: Visão geral de RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: bfed42bcf3693ef744b3ed2b54ebe070931513a9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855739"
---
# <a name="richtextbox-overview"></a>Visão geral de RichTextBox

O <xref:System.Windows.Controls.RichTextBox> controle permite exibir ou editar o conteúdo do fluxo, incluindo parágrafos, imagens, tabelas e muito mais. Este tópico apresenta a <xref:System.Windows.Controls.TextBox> classe e fornece exemplos de como usá-la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] no e C#no.

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox?

Ambos <xref:System.Windows.Controls.RichTextBox> e<xref:System.Windows.Controls.TextBox> permitem que os usuários editem texto, no entanto, os dois controles são usados em cenários diferentes. R <xref:System.Windows.Controls.RichTextBox> é uma opção melhor quando é necessário que o usuário edite texto formatado, imagens, tabelas ou outros conteúdos avançados. Por exemplo, a edição de um documento, artigo ou blog que requer formatação, imagens etc. é melhor realizada usando <xref:System.Windows.Controls.RichTextBox>um. R <xref:System.Windows.Controls.TextBox> requer menos recursos do sistema <xref:System.Windows.Controls.RichTextBox> , e é ideal quando apenas texto sem formatação precisa ser editado (ou seja, uso em formulários). Consulte [visão geral da caixa](textbox-overview.md) de texto <xref:System.Windows.Controls.TextBox>para obter mais informações. A tabela a seguir resume os principais recursos do <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox>do.

|Controle|Correção ortográfica em tempo real|O menu de contexto|Formatando comandos <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> como (CTR + B)|<xref:System.Windows.Documents.FlowDocument>conteúdo como imagens, parágrafos, tabelas, etc.|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|Sim|Sim|Não|Nº|
|<xref:System.Windows.Controls.RichTextBox>|Sim|Sim|Sim|Sim|

> [!NOTE]
> Embora <xref:System.Windows.Controls.TextBox> o não ofereça suporte <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>a comandos relacionados <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> à formatação como (CTR + B), muitos comandos básicos têm suporte em ambos os controles, como.

Os recursos da tabela acima são abordados em mais detalhes posteriormente.

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a>Criando um RichTextBox

O código a seguir mostra como criar um <xref:System.Windows.Controls.RichTextBox> que um usuário pode editar conteúdo rico no.

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

Especificamente, o conteúdo editado em <xref:System.Windows.Controls.RichTextBox> um é conteúdo de fluxo. O conteúdo de fluxo pode conter vários tipos de elementos incluindo texto formatado, imagens, listas e tabelas. Consulte [Visão geral de documento dinâmico](../advanced/flow-document-overview.md) para obter informações aprofundadas sobre documentos de fluxo. Para conter conteúdo de fluxo, um <xref:System.Windows.Controls.RichTextBox> hospeda um <xref:System.Windows.Documents.FlowDocument> objeto que, por sua vez, contém o conteúdo editável. Para demonstrar o conteúdo do Flow <xref:System.Windows.Controls.RichTextBox>em um, o código a seguir mostra como <xref:System.Windows.Controls.RichTextBox> criar um com um parágrafo e um texto em negrito.

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

A ilustração a seguir mostra como esse exemplo é renderizado.

![RichTextBox com conteúdo](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")

Elementos como <xref:System.Windows.Documents.Paragraph> e <xref:System.Windows.Documents.Bold> determinam como o conteúdo dentro <xref:System.Windows.Controls.RichTextBox> de um é exibido. Como um usuário edita <xref:System.Windows.Controls.RichTextBox> o conteúdo, ele altera esse conteúdo do fluxo. Para saber mais sobre os recursos do conteúdo de fluxo e como trabalhar com ele, consulte [Visão geral de documento de fluxo](../advanced/flow-document-overview.md).

> [!NOTE]
> O conteúdo de fluxo <xref:System.Windows.Controls.RichTextBox> dentro de um não se comporta exatamente como conteúdo de fluxo contido em outros controles. Por exemplo, não há colunas em um <xref:System.Windows.Controls.RichTextBox> e, portanto, nenhum comportamento de redimensionamento automático. Além disso, recursos internos como pesquisa, modo de exibição, navegação de página e zoom não estão disponíveis em <xref:System.Windows.Controls.RichTextBox>um.

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a>Correção ortográfica em tempo real

Você pode habilitar a verificação ortográfica em tempo real em <xref:System.Windows.Controls.TextBox> um <xref:System.Windows.Controls.RichTextBox>ou. Quando a verificação ortográfica está ativada, uma linha vermelha aparecerá sob as palavras incorretas (veja a figura abaixo).

![Caixa de texto com verificação ortográfica](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")

Consulte [Habilitar verificação ortográfica em um controle de edição de texto](how-to-enable-spell-checking-in-a-text-editing-control.md) para saber como habilitar a verificação ortográfica.

<a name="context_menu"></a>

## <a name="context-menu"></a>O menu de contexto

Por padrão, <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox> têm um menu de contexto que aparece quando um usuário clica com o botão direito do mouse dentro do controle. O menu de contexto permite ao usuário recortar, copiar ou colar (veja a figura abaixo).

![TextBox com menu de contexto](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")

Você pode criar seu próprio menu de contexto personalizado para substituir o padrão. Consulte [Posicionar um menu de contexto personalizado em um RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md) para obter mais informações.

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a>Comando de Edição

Os comandos de edição permitem que os usuários formatem <xref:System.Windows.Controls.RichTextBox>conteúdo editável dentro de um. Além dos comandos de edição <xref:System.Windows.Controls.RichTextBox> básicos, o inclui <xref:System.Windows.Controls.TextBox> comandos de formatação que não dão suporte ao. Por exemplo, ao editar em um <xref:System.Windows.Controls.RichTextBox>, um usuário poderia pressionar CTR + B para alternar a formatação de texto em negrito. Consulte <xref:System.Windows.Documents.EditingCommands> para obter uma lista completa de comandos disponíveis. Além de usar atalhos de teclado, você pode associar comandos com outros controles como botões. O exemplo a seguir mostra como criar uma barra de ferramentas simples contendo botões que o usuário pode usar para alterar a formatação de texto.

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

A ilustração a seguir mostra como esse exemplo é exibido.

![RichTextBox com ToolBar](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a>Detectar quando o conteúdo é alterado

Normalmente, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> o evento deve ser usado para detectar sempre que o texto <xref:System.Windows.Controls.TextBox> em <xref:System.Windows.Controls.RichTextBox> um ou é <xref:System.Windows.UIElement.KeyDown> alterado, em vez disso, como você pode esperar. Consulte [Como detectar quando o texto em um TextBox foi alterado](how-to-detect-when-text-in-a-textbox-has-changed.md) para ver um exemplo.

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a>Salvar, carregar e imprimir conteúdo RichTextBox

O exemplo a seguir mostra como salvar o conteúdo de <xref:System.Windows.Controls.RichTextBox> um em um arquivo, carregar esse conteúdo de volta <xref:System.Windows.Controls.RichTextBox>no e imprimir o conteúdo. Abaixo está a marcação para o exemplo.

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

Abaixo está o código anterior para o exemplo.

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a>Consulte também

- [Tópicos de instruções](richtextbox-how-to-topics.md)
- [Visão geral de TextBox](textbox-overview.md)
