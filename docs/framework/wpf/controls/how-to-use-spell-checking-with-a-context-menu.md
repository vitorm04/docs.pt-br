---
title: "Como usar verificação ortográfica com um menu de contexto"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a85426dc526e1e8560f494bcde5247fc394f7bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>Como usar verificação ortográfica com um menu de contexto
Por padrão, quando você habilitar a verificação ortográfica em um controle de edição como <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox>, você obtém opções de verificação ortográfica no menu de contexto. Por exemplo, quando os usuários clicam com o botão direito do mouse em uma palavra incorreta, eles recebem um conjunto de sugestões de ortografia ou a opção de **Ignorar tudo**. No entanto, quando você substituir o menu de contexto padrão pelo seu próprio menu de contexto personalizado, essa funcionalidade será perdida e você precisará escrever o código para reabilitar o recurso de verificação ortográfica no menu de contexto. O exemplo a seguir mostra como ativar isso em um <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que cria um <xref:System.Windows.Controls.TextBox> com alguns eventos que são usados para implementar o menu de contexto.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o código que implementa o menu de contexto.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 O código usado para fazer isso com um <xref:System.Windows.Controls.RichTextBox> é semelhante. A principal diferença está no parâmetro passado para o método `GetSpellingError`. Para um <xref:System.Windows.Controls.TextBox>, passe o índice inteiro da posição do cursor:  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 Para uma <xref:System.Windows.Controls.RichTextBox>, passar o <xref:System.Windows.Documents.TextPointer> que especifica a posição do cursor:  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Habilitar verificação ortográfica em um controle de edição de texto](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [Usar um menu de contexto personalizado com um TextBox](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
