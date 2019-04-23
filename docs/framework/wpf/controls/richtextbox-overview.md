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
ms.openlocfilehash: 9aa0d33b3cb2c15ba9c1cb7e7d7be9a3125f66d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162700"
---
# <a name="richtextbox-overview"></a>Visão geral de RichTextBox
O <xref:System.Windows.Controls.RichTextBox> controle permite que você exiba ou edite o conteúdo de fluxo, incluindo parágrafos, imagens, tabelas e muito mais. Este tópico apresenta os <xref:System.Windows.Controls.TextBox> de classe e fornece exemplos de como usá-lo em ambos [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e C#.  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox?  
 Ambos <xref:System.Windows.Controls.RichTextBox> e <xref:System.Windows.Controls.TextBox> permitir aos usuários editar texto, no entanto, os dois controles são usados em cenários diferentes. Um <xref:System.Windows.Controls.RichTextBox> é uma opção melhor quando é necessário que o usuário edite texto formatado, imagens, tabelas ou outros conteúdos avançados. Por exemplo, editar um documento, artigo ou blog que requer formatação, imagens, etc é melhor realizada usando um <xref:System.Windows.Controls.RichTextBox>. Um <xref:System.Windows.Controls.TextBox> requer menos recursos do sistema, um <xref:System.Windows.Controls.RichTextBox> e é ideal quando apenas texto sem formatação precisa ser editado (isto é, uso em formulários). Ver [visão geral de TextBox](textbox-overview.md) para obter mais informações sobre <xref:System.Windows.Controls.TextBox>. A tabela abaixo resume os principais recursos do <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox>.  
  
|Controle|Correção ortográfica em tempo real|O menu de contexto|Comandos de formatação como <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr + B)|<xref:System.Windows.Documents.FlowDocument> conteúdo como imagens, parágrafos, tabelas, etc.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Sim|Sim|Não|Nº|  
|<xref:System.Windows.Controls.RichTextBox>|Sim|Sim|Sim|Sim|  
  
 **Observação:** Embora <xref:System.Windows.Controls.TextBox> não oferece suporte a comandos relacionados, como a formatação <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr + B), muitos comandos básicos têm suporte em ambos os controles, como <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  
  
 Os recursos da tabela acima são abordados em mais detalhes posteriormente.  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>Criando um RichTextBox  
 O código a seguir mostra como criar um <xref:System.Windows.Controls.RichTextBox> que um usuário pode editar conteúdo avançado no.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 Especificamente, o conteúdo editado em uma <xref:System.Windows.Controls.RichTextBox> é o conteúdo de fluxo. O conteúdo de fluxo pode conter vários tipos de elementos incluindo texto formatado, imagens, listas e tabelas. Consulte [Visão geral de documento dinâmico](../advanced/flow-document-overview.md) para obter informações aprofundadas sobre documentos de fluxo. Para conter conteúdo de fluxo, uma <xref:System.Windows.Controls.RichTextBox> hospeda um <xref:System.Windows.Documents.FlowDocument> objeto que contém o conteúdo editável. Para demonstrar o fluxo de conteúdo em um <xref:System.Windows.Controls.RichTextBox>, o código a seguir mostra como criar um <xref:System.Windows.Controls.RichTextBox> com um parágrafo e texto em negrito.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 A ilustração a seguir mostra como esse exemplo é renderizado.  
  
 ![RichTextBox com conteúdo](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 Elementos como <xref:System.Windows.Documents.Paragraph> e <xref:System.Windows.Documents.Bold> determinar como o conteúdo dentro de um <xref:System.Windows.Controls.RichTextBox> é exibida. Conforme um usuário edita <xref:System.Windows.Controls.RichTextBox> conteúdo, eles alteram o conteúdo de fluxo. Para saber mais sobre os recursos do conteúdo de fluxo e como trabalhar com ele, consulte [Visão geral de documento de fluxo](../advanced/flow-document-overview.md).  
  
 **Observação:** Fluxo de conteúdo dentro de um <xref:System.Windows.Controls.RichTextBox> não se comporta exatamente como o conteúdo de fluxo contido em outros controles. Por exemplo, não há nenhuma coluna em um <xref:System.Windows.Controls.RichTextBox> e, portanto, o comportamento de redimensionamento não automática. Além disso, recursos internos, como pesquisa, modo de exibição, navegação de página e zoom não estão disponíveis em um <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>Correção ortográfica em tempo real  
 Você pode habilitar verificação ortográfica em tempo real um <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox>. Quando a verificação ortográfica está ativada, uma linha vermelha aparecerá sob as palavras incorretas (veja a figura abaixo).  
  
 ![Caixa de texto com verificação ortográfica](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Consulte [Habilitar verificação ortográfica em um controle de edição de texto](how-to-enable-spell-checking-in-a-text-editing-control.md) para saber como habilitar a verificação ortográfica.  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>O menu de contexto  
 Por padrão, ambos <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox> têm um menu de contexto que aparece quando um usuário clica com o botão direito dentro do controle. O menu de contexto permite ao usuário recortar, copiar ou colar (veja a figura abaixo).  
  
 ![TextBox com menu de contexto](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Você pode criar seu próprio menu de contexto personalizado para substituir o padrão. Consulte [Posicionar um menu de contexto personalizado em um RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md) para obter mais informações.  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>Comando de Edição  
 Comandos de edição permitem que os usuários formatem conteúdo editável em um <xref:System.Windows.Controls.RichTextBox>. Edição de comandos, além de basic <xref:System.Windows.Controls.RichTextBox> inclui comandos de formatação que <xref:System.Windows.Controls.TextBox> não oferece suporte. Por exemplo, quando a edição em um <xref:System.Windows.Controls.RichTextBox>, um usuário poderia pressionar CTRL + B para alternar a formatação de texto em negrito. Consulte <xref:System.Windows.Documents.EditingCommands> para obter uma lista completa dos comandos disponíveis. Além de usar atalhos de teclado, você pode associar comandos com outros controles como botões. O exemplo a seguir mostra como criar uma barra de ferramentas simples contendo botões que o usuário pode usar para alterar a formatação de texto.  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 A ilustração a seguir mostra como esse exemplo é exibido.  
  
 ![RichTextBox com ToolBar](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Detectar quando o conteúdo é alterado  
 Normalmente o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento deve ser usado para detectar sempre que o texto em um <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox> muda, em seguida, em vez disso, <xref:System.Windows.UIElement.KeyDown> como esperado. Consulte [Como detectar quando o texto em um TextBox foi alterado](how-to-detect-when-text-in-a-textbox-has-changed.md) para ver um exemplo.  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>Salvar, carregar e imprimir conteúdo RichTextBox  
 O exemplo a seguir mostra como salvar o conteúdo de um <xref:System.Windows.Controls.RichTextBox> em um arquivo, carregar esse conteúdo de volta para o <xref:System.Windows.Controls.RichTextBox>e imprimir o conteúdo. Abaixo está a marcação para o exemplo.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 Abaixo está o código anterior para o exemplo.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Tópicos de instruções](richtextbox-how-to-topics.md)
- [Visão geral de TextBox](textbox-overview.md)
