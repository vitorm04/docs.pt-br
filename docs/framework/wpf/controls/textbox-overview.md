---
title: Visão geral de TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: bb03d09b1730f4a8d607773f9024eee4f125e2c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557765"
---
# <a name="textbox-overview"></a>Visão geral de TextBox
O <xref:System.Windows.Controls.TextBox> classe permite que você exiba ou edite o texto não formatado. Um uso comum de um <xref:System.Windows.Controls.TextBox> está editando o texto não formatado em um formulário. Por exemplo, um formulário solicitando o nome do usuário, número de telefone, etc. usaria <xref:System.Windows.Controls.TextBox> controles de entrada de texto. Este tópico apresenta o <xref:System.Windows.Controls.TextBox> classe e fornece exemplos de como usá-lo no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e c#.  
  
 
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox?  
 Ambos <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox> permitem que os usuários para texto de entrada, mas os dois controles são usados para cenários diferentes. Um <xref:System.Windows.Controls.TextBox> requer menos recursos do sistema, um <xref:System.Windows.Controls.RichTextBox> então é o ideal quando apenas texto sem formatação precisa ser editado (isto é, uso em um formulário). A <xref:System.Windows.Controls.RichTextBox> é uma opção melhor quando é necessário que o usuário edite texto formatado, imagens, tabelas ou outras suporte para conteúdo. Por exemplo, a edição de um documento, artigo ou blog que requer formatação, imagens, etc. é melhor realizada usando um <xref:System.Windows.Controls.RichTextBox>. A tabela a seguir resume os principais recursos de <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.TextBox>.  
  
|Controle|Correção ortográfica em tempo real|O menu de contexto|Os comandos de formatação <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr + B)|<xref:System.Windows.Documents.FlowDocument> conteúdo, como imagens, parágrafos, tabelas, etc.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Sim|Sim|Não|Nº|  
|<xref:System.Windows.Controls.RichTextBox>|Sim|Sim|Sim (consulte [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|Sim (consulte [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|  
  
> [!NOTE]
>  Embora <xref:System.Windows.Controls.TextBox> faz comandos não dá suporte a edição relacionados a formatação como <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr + B), muitos comandos básicos são suportados por ambos os controles, como <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>. Consulte <xref:System.Windows.Documents.EditingCommands> para obter mais informações.  
  
 Recursos com suporte <xref:System.Windows.Controls.TextBox> são abordados nas seções a seguir. Para obter mais informações sobre <xref:System.Windows.Controls.RichTextBox>, consulte [visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Correção ortográfica em tempo real  
 Você pode habilitar correção ortográfica em tempo real em um <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox>. Quando a verificação ortográfica está ativada, uma linha vermelha aparecerá sob as palavras incorretas (veja a figura abaixo).  
  
 ![Caixa de texto com verificação ortográfica](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Consulte [Habilitar verificação ortográfica em um controle de edição de texto](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md) para saber como habilitar a verificação ortográfica.  
  
### <a name="context-menu"></a>O menu de contexto  
 Por padrão, ambos <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox> têm um menu de contexto que aparece quando um usuário clica com o botão direito dentro do controle. O menu de contexto permite ao usuário recortar, copiar ou colar (veja a figura abaixo).  
  
 ![TextBox com menu de contexto](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Você pode criar seu próprio menu de contexto personalizado para substituir o comportamento padrão. Consulte [Usar um menu de contexto personalizado com um TextBox](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md) para obter mais informações.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Criando TextBoxes  
 Um <xref:System.Windows.Controls.TextBox> pode ser uma única linha de altura ou abranger várias linhas. Uma única linha <xref:System.Windows.Controls.TextBox> é melhor para a entrada de pequenas quantidades de texto sem formatação (ou seja, “Nome”, “Número de Telefone”, etc. em um formulário). O exemplo a seguir mostra como criar uma única linha <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Você também pode criar um <xref:System.Windows.Controls.TextBox> que permite que o usuário insira várias linhas de texto. Por exemplo, se o formulário solicita um esboço biografia do usuário, você usaria uma <xref:System.Windows.Controls.TextBox> que dá suporte a várias linhas de texto. O exemplo a seguir mostra como usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir um <xref:System.Windows.Controls.TextBox> controle que se expande automaticamente para acomodar várias linhas de texto.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Definindo o <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributo `Wrap` faz com que o texto passe para uma nova linha quando a borda do <xref:System.Windows.Controls.TextBox> controle é alcançado, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> controle para incluir espaço para uma nova linha, se necessário.  
  
 Definindo o <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributo `true` faz com que uma nova linha seja inserida quando a tecla é pressionada, outra vez automaticamente expandindo o <xref:System.Windows.Controls.TextBox> para incluir espaço para uma nova linha, se necessário.  
  
 O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma barra de rolagem para o <xref:System.Windows.Controls.TextBox>, de modo que o conteúdo do <xref:System.Windows.Controls.TextBox> pode ser rolado por meio de se o <xref:System.Windows.Controls.TextBox> expande além do tamanho do quadro ou janela que inclui-lo.  
  
 Para obter mais informações sobre diferentes tarefas associadas ao uso de um <xref:System.Windows.Controls.TextBox>, consulte [tópicos de instruções](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Detectar quando o conteúdo é alterado  
 Geralmente o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento deve ser usado para detectar sempre que o texto em uma <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox> for alterado, em vez disso, em seguida, <xref:System.Windows.UIElement.KeyDown> como esperado. Consulte [Como detectar quando o texto em um TextBox foi alterado](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md) para ver um exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
