---
title: Visão geral de TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 46600fd1a3023a80d49fae6f020279be6131916a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951480"
---
# <a name="textbox-overview"></a>Visão geral de TextBox
A <xref:System.Windows.Controls.TextBox> classe permite que você exiba ou edite texto não formatado. Um uso comum de um <xref:System.Windows.Controls.TextBox> é a edição de texto não formatado em um formulário. Por exemplo, um formulário solicitando o nome do usuário, o número de telefone, etc <xref:System.Windows.Controls.TextBox> ., usaria controles para entrada de texto. Este tópico apresenta a <xref:System.Windows.Controls.TextBox> classe e fornece exemplos de como usá-la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] no e C#no.  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox?  
 Ambos <xref:System.Windows.Controls.TextBox> e<xref:System.Windows.Controls.RichTextBox> permitem que os usuários insiram texto, mas os dois controles são usados para cenários diferentes. R <xref:System.Windows.Controls.TextBox> requer menos recursos do sistema <xref:System.Windows.Controls.RichTextBox> , então, é ideal quando apenas texto sem formatação precisa ser editado (ou seja, uso em um formulário). R <xref:System.Windows.Controls.RichTextBox> é uma opção melhor quando é necessário que o usuário edite texto formatado, imagens, tabelas ou outro conteúdo com suporte. Por exemplo, a edição de um documento, artigo ou blog que requer formatação, imagens etc. é melhor realizada usando <xref:System.Windows.Controls.RichTextBox>um. A tabela a seguir resume os principais recursos do <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.TextBox>do.  
  
|Controle|Correção ortográfica em tempo real|O menu de contexto|Formatando comandos <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> como (CTR + B)|<xref:System.Windows.Documents.FlowDocument>conteúdo como imagens, parágrafos, tabelas, etc.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Sim|Sim|Não|Nº|  
|<xref:System.Windows.Controls.RichTextBox>|Sim|Sim|Sim (consulte [Visão geral de RichTextBox](richtextbox-overview.md))|Sim (consulte [Visão geral de RichTextBox](richtextbox-overview.md))|  
  
> [!NOTE]
> Embora <xref:System.Windows.Controls.TextBox> o não ofereça suporte à formatação de comandos <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> de edição relacionados como (CTR + B), muitos comandos básicos têm suporte <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>em ambos os controles, como. Consulte <xref:System.Windows.Documents.EditingCommands> para obter mais informações.  
  
 Os recursos com <xref:System.Windows.Controls.TextBox> suporte do são abordados nas seções a seguir. Para obter mais informações <xref:System.Windows.Controls.RichTextBox>sobre, consulte [visão geral de RichTextBox](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Correção ortográfica em tempo real  
 Você pode habilitar a correção ortográfica em tempo real em <xref:System.Windows.Controls.TextBox> um <xref:System.Windows.Controls.RichTextBox>ou. Quando a verificação ortográfica está ativada, uma linha vermelha aparecerá sob as palavras incorretas (veja a figura abaixo).  
  
 ![Caixa de texto com verificação ortográfica](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Consulte [Habilitar verificação ortográfica em um controle de edição de texto](how-to-enable-spell-checking-in-a-text-editing-control.md) para saber como habilitar a verificação ortográfica.  
  
### <a name="context-menu"></a>O menu de contexto  
 Por padrão, <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox> têm um menu de contexto que aparece quando um usuário clica com o botão direito do mouse dentro do controle. O menu de contexto permite ao usuário recortar, copiar ou colar (veja a figura abaixo).  
  
 ![TextBox com menu de contexto](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Você pode criar seu próprio menu de contexto personalizado para substituir o comportamento padrão. Consulte [Usar um menu de contexto personalizado com um TextBox](how-to-use-a-custom-context-menu-with-a-textbox.md) para obter mais informações.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Criando TextBoxes  
 Um <xref:System.Windows.Controls.TextBox> pode ser uma única linha em altura ou conter várias linhas. Uma única linha <xref:System.Windows.Controls.TextBox> é melhor para inserir pequenas quantidades de texto sem formatação (ou seja, “Nome”, “Número de Telefone”, etc. em um formulário). O exemplo a seguir mostra como criar uma única linha <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Você também pode criar um <xref:System.Windows.Controls.TextBox> que permita que o usuário insira várias linhas de texto. Por exemplo, se seu formulário solicitou um esboço de meio-gráfico do usuário, você desejaria usar um <xref:System.Windows.Controls.TextBox> que dê suporte a várias linhas de texto. O exemplo a seguir mostra como usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] o para definir <xref:System.Windows.Controls.TextBox> um controle que se expande automaticamente para acomodar várias linhas de texto.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Definir o <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributo para `Wrap` faz com que o texto seja quebrado em uma nova linha <xref:System.Windows.Controls.TextBox> quando a borda do controle for atingida, <xref:System.Windows.Controls.TextBox> expandindo automaticamente o controle para incluir espaço para uma nova linha, se necessário.  
  
 Definir o <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributo como `true` faz com que uma nova linha seja inserida quando a tecla de retorno é pressionada, mais <xref:System.Windows.Controls.TextBox> uma vez automaticamente expandindo a sala de inclusão para uma nova linha, se necessário.  
  
 O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma barra de rolagem <xref:System.Windows.Controls.TextBox>ao, para <xref:System.Windows.Controls.TextBox> que o conteúdo do possa ser rolado por meio de <xref:System.Windows.Controls.TextBox> se expandir para além do tamanho do quadro ou da janela que o inclui.  
  
 Para obter mais informações sobre tarefas diferentes associadas ao uso <xref:System.Windows.Controls.TextBox>de um, consulte os [Tópicos de instruções](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Detectar quando o conteúdo é alterado  
 Normalmente, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> o evento deve ser usado para detectar sempre que o texto <xref:System.Windows.Controls.TextBox> em <xref:System.Windows.Controls.RichTextBox> uma <xref:System.Windows.UIElement.KeyDown> ou é alterado, em vez disso, como você pode esperar. Consulte [Como detectar quando o texto em um TextBox foi alterado](how-to-detect-when-text-in-a-textbox-has-changed.md) para ver um exemplo.  
  
## <a name="see-also"></a>Consulte também

- [Tópicos de instruções](textbox-how-to-topics.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
