---
title: Visão geral de TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 9fbae5ac4de4c78a1086bcbd9bfc9e01eb597fb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186636"
---
# <a name="textbox-overview"></a>Visão geral de TextBox
A <xref:System.Windows.Controls.TextBox> classe permite que você exiba ou edite texto não formatado. Um uso comum de um <xref:System.Windows.Controls.TextBox> é editar texto não formatado em um formulário. Por exemplo, um formulário pedindo o nome do usuário, <xref:System.Windows.Controls.TextBox> número de telefone, etc. usaria controles para entrada de texto. Este tópico introduz <xref:System.Windows.Controls.TextBox> a classe e fornece exemplos de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] como usá-lo em ambos e C#.  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox?  
 Ambos <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> permitem que os usuários insiram texto, mas os dois controles são usados para diferentes cenários. A <xref:System.Windows.Controls.TextBox> requer menos recursos <xref:System.Windows.Controls.RichTextBox> do sistema do que um, portanto, é ideal quando apenas texto simples precisa ser editado (ou seja, uso em um formulário). A <xref:System.Windows.Controls.RichTextBox> é uma escolha melhor quando é necessário para o usuário editar texto formatado, imagens, tabelas ou outro conteúdo suportado. Por exemplo, editar um documento, artigo ou blog que exija formatação, <xref:System.Windows.Controls.RichTextBox>imagens, etc. é melhor realizado usando um . A tabela abaixo resume as <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox>características primárias de e .  
  
|Control|Correção ortográfica em tempo real|Menu de contexto|Comandos de <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> formatação como (Ctr+B)|<xref:System.Windows.Documents.FlowDocument>conteúdo como imagens, parágrafos, tabelas, etc.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Sim|Sim|Não|Não.|  
|<xref:System.Windows.Controls.RichTextBox>|Sim|Sim|Sim (consulte [Visão geral de RichTextBox](richtextbox-overview.md))|Sim (consulte [Visão geral de RichTextBox](richtextbox-overview.md))|  
  
> [!NOTE]
> Embora <xref:System.Windows.Controls.TextBox> não suporte comandos de edição <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> relacionados à formatação como (Ctr+B), muitos <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>comandos básicos são suportados por ambos os controles, tais como . Consulte <xref:System.Windows.Documents.EditingCommands> para obter mais informações.  
  
 Os recursos <xref:System.Windows.Controls.TextBox> suportados são cobertos nas seções abaixo. Para obter <xref:System.Windows.Controls.RichTextBox>mais informações sobre, consulte [RichTextBox Overview](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Correção ortográfica em tempo real  
 Você pode habilitar a verificação <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox>ortonada em tempo real em um ou . Quando a verificação ortográfica está ativada, uma linha vermelha aparecerá sob as palavras incorretas (veja a figura abaixo).  
  
 ![Caixa de texto com verificação de&#45;ortodial](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Consulte [Habilitar verificação ortográfica em um controle de edição de texto](how-to-enable-spell-checking-in-a-text-editing-control.md) para saber como habilitar a verificação ortográfica.  
  
### <a name="context-menu"></a>Menu de contexto  
 Por padrão, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> ambos e ter um menu de contexto que aparece quando um usuário clica com o botão direito do mouse dentro do controle. O menu de contexto permite ao usuário recortar, copiar ou colar (veja a figura abaixo).  
  
 ![TextBox com menu de contexto](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Você pode criar seu próprio menu de contexto personalizado para substituir o comportamento padrão. Consulte [Usar um menu de contexto personalizado com um TextBox](how-to-use-a-custom-context-menu-with-a-textbox.md) para obter mais informações.  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>Criando TextBoxes  
 A <xref:System.Windows.Controls.TextBox> pode ser uma única linha de altura ou compreender várias linhas. Uma única <xref:System.Windows.Controls.TextBox> linha é melhor para inserir pequenas quantidades de texto simples (ou seja, "Nome", "Número de Telefone", etc. em um formulário). O exemplo a seguir mostra <xref:System.Windows.Controls.TextBox>como criar uma única linha .  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Você também pode <xref:System.Windows.Controls.TextBox> criar um que permite ao usuário inserir várias linhas de texto. Por exemplo, se o seu formulário pediu um esboço biográfico <xref:System.Windows.Controls.TextBox> do usuário, você gostaria de usar um que suporte várias linhas de texto. O exemplo a seguir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] mostra <xref:System.Windows.Controls.TextBox> como usar para definir um controle que se expande automaticamente para acomodar várias linhas de texto.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Definir <xref:System.Windows.Controls.TextBox.TextWrapping%2A> o `Wrap` atributo para fazer com que o <xref:System.Windows.Controls.TextBox> texto seja embrulhado para uma <xref:System.Windows.Controls.TextBox> nova linha quando a borda do controle for atingida, expandindo automaticamente o controle para incluir espaço para uma nova linha, se necessário.  
  
 Definir <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> o `true` atributo para faz com que uma nova linha seja inserida quando <xref:System.Windows.Controls.TextBox> a tecla RETURN é pressionada, expandindo novamente automaticamente o espaço para incluir uma nova linha, se necessário.  
  
 O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma <xref:System.Windows.Controls.TextBox>barra de rolagem <xref:System.Windows.Controls.TextBox> ao , de modo <xref:System.Windows.Controls.TextBox> que o conteúdo do pode ser rolado através se o expande além do tamanho do quadro ou janela que o inclui.  
  
 Para obter mais informações sobre <xref:System.Windows.Controls.TextBox>diferentes tarefas associadas ao uso de um , consulte [Como fazer tópicos](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>Detectar quando o conteúdo é alterado  
 Normalmente, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> o evento deve ser usado <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> para detectar <xref:System.Windows.UIElement.KeyDown> sempre que o texto em um ou altera, em vez disso, como você pode esperar. Consulte [Como detectar quando o texto em um TextBox foi alterado](how-to-detect-when-text-in-a-textbox-has-changed.md) para ver um exemplo.  
  
## <a name="see-also"></a>Confira também

- [Tópicos de como fazer](textbox-how-to-topics.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
