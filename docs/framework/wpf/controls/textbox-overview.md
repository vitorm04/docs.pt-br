---
title: Visão geral de TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 577a12a0c04e5e3bfbfecb2c45263b684f0ffc17
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162640"
---
# <a name="textbox-overview"></a>Visão geral de TextBox
O <xref:System.Windows.Controls.TextBox> classe permite que você exiba ou edite texto não formatado. Um uso comum de um <xref:System.Windows.Controls.TextBox> está editando o texto não formatado em um formulário. Por exemplo, um formulário que solicita o nome do usuário, número de telefone, etc. usaria <xref:System.Windows.Controls.TextBox> controles de entrada de texto. Este tópico apresenta os <xref:System.Windows.Controls.TextBox> de classe e fornece exemplos de como usá-lo em ambos [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e C#.  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox?  
 Ambos <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox> permitem aos usuários inserir texto, mas os dois controles são usados para cenários diferentes. Um <xref:System.Windows.Controls.TextBox> requer menos recursos do sistema, um <xref:System.Windows.Controls.RichTextBox> para que ele é ideal quando apenas texto sem formatação precisa ser editado (isto é, uso em um formulário). Um <xref:System.Windows.Controls.RichTextBox> é uma opção melhor quando é necessário que o usuário edite texto formatado, imagens, tabelas ou outros com suporte conteúda. Por exemplo, editar um documento, artigo ou blog que requer formatação, imagens, etc é melhor realizada usando um <xref:System.Windows.Controls.RichTextBox>. A tabela abaixo resume os principais recursos do <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.TextBox>.  
  
|Controle|Correção ortográfica em tempo real|O menu de contexto|Comandos de formatação como <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr + B)|<xref:System.Windows.Documents.FlowDocument> conteúdo como imagens, parágrafos, tabelas, etc.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Sim|Sim|Não|Nº|  
|<xref:System.Windows.Controls.RichTextBox>|Sim|Sim|Sim (consulte [Visão geral de RichTextBox](richtextbox-overview.md))|Sim (consulte [Visão geral de RichTextBox](richtextbox-overview.md))|  
  
> [!NOTE]
>  Embora <xref:System.Windows.Controls.TextBox> faz não dão suporte a edição relacionados a formatação de comandos, como <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr + B), muitos comandos básicos têm suporte em ambos os controles, como <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>. Consulte <xref:System.Windows.Documents.EditingCommands> para obter mais informações.  
  
 Recursos suportados pelo <xref:System.Windows.Controls.TextBox> são abordados nas seções a seguir. Para obter mais informações sobre <xref:System.Windows.Controls.RichTextBox>, consulte [visão geral de RichTextBox](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Correção ortográfica em tempo real  
 Você pode habilitar a verificação ortográfica em tempo real em um <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox>. Quando a verificação ortográfica está ativada, uma linha vermelha aparecerá sob as palavras incorretas (veja a figura abaixo).  
  
 ![Caixa de texto com verificação ortográfica](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Consulte [Habilitar verificação ortográfica em um controle de edição de texto](how-to-enable-spell-checking-in-a-text-editing-control.md) para saber como habilitar a verificação ortográfica.  
  
### <a name="context-menu"></a>O menu de contexto  
 Por padrão, ambos <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox> têm um menu de contexto que aparece quando um usuário clica com o botão direito dentro do controle. O menu de contexto permite ao usuário recortar, copiar ou colar (veja a figura abaixo).  
  
 ![TextBox com menu de contexto](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Você pode criar seu próprio menu de contexto personalizado para substituir o comportamento padrão. Consulte [Usar um menu de contexto personalizado com um TextBox](how-to-use-a-custom-context-menu-with-a-textbox.md) para obter mais informações.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Criando TextBoxes  
 Um <xref:System.Windows.Controls.TextBox> pode ser uma única linha de altura ou abranger várias linhas. Uma única linha <xref:System.Windows.Controls.TextBox> é melhor para a entrada de pequenas quantidades de texto sem formatação (ou seja, “Nome”, “Número de Telefone”, etc. em um formulário). O exemplo a seguir mostra como criar uma única linha <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Você também pode criar um <xref:System.Windows.Controls.TextBox> que permite que o usuário insira várias linhas de texto. Por exemplo, se o formulário solicitou um esboço da biografia do usuário, você iria querer usar um <xref:System.Windows.Controls.TextBox> que dá suporte a várias linhas de texto. O exemplo a seguir mostra como usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir um <xref:System.Windows.Controls.TextBox> controle que se expande automaticamente para acomodar várias linhas de texto.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Definindo o <xref:System.Windows.Controls.TextBox.TextWrapping%2A> de atributo para `Wrap` faz com que o texto quebre para uma nova linha quando a borda da <xref:System.Windows.Controls.TextBox> controle é alcançada, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> controle para incluir espaço para uma nova linha, se necessário.  
  
 Definindo o <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> de atributo para `true` faz com que uma nova linha seja inserida quando a tecla RETURN é pressionada, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> para incluir espaço para uma nova linha, se necessário.  
  
 O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma barra de rolagem para o <xref:System.Windows.Controls.TextBox>, de modo que o conteúdo da <xref:System.Windows.Controls.TextBox> poderá ser rolado se o <xref:System.Windows.Controls.TextBox> ultrapassar o tamanho do quadro ou janela que o contém.  
  
 Para obter mais informações sobre as diferentes tarefas associadas ao uso de um <xref:System.Windows.Controls.TextBox>, consulte [tópicos de instruções](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Detectar quando o conteúdo é alterado  
 Normalmente, o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento deve ser usado para detectar sempre que o texto em um <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox> for alterado, em vez disso, em seguida, <xref:System.Windows.UIElement.KeyDown> como você pode esperar. Consulte [Como detectar quando o texto em um TextBox foi alterado](how-to-detect-when-text-in-a-textbox-has-changed.md) para ver um exemplo.  
  
## <a name="see-also"></a>Consulte também

- [Tópicos de instruções](textbox-how-to-topics.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
