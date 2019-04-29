---
title: 'Como: Usar verificação ortográfica com um menu de contexto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 72b24c386eb99140c9c2729688994b81f92e1a6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699143"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a><span data-ttu-id="f2038-102">Como: Usar verificação ortográfica com um menu de contexto</span><span class="sxs-lookup"><span data-stu-id="f2038-102">How to: Use Spell Checking with a Context Menu</span></span>
<span data-ttu-id="f2038-103">Por padrão, como quando você habilita a verificação ortográfica em um controle de edição <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox>, você obtém opções de verificação ortográfica no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="f2038-103">By default, when you enable spell checking in an editing control like <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>, you get spell-checking choices in the context menu.</span></span> <span data-ttu-id="f2038-104">Por exemplo, quando os usuários clicam com o botão direito do mouse em uma palavra incorreta, eles recebem um conjunto de sugestões de ortografia ou a opção de **Ignorar tudo**.</span><span class="sxs-lookup"><span data-stu-id="f2038-104">For example, when users right-click a misspelled word, they get a set of spelling suggestions or the option to **Ignore All**.</span></span> <span data-ttu-id="f2038-105">No entanto, quando você substituir o menu de contexto padrão pelo seu próprio menu de contexto personalizado, essa funcionalidade será perdida e você precisará escrever o código para reabilitar o recurso de verificação ortográfica no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="f2038-105">However, when you override the default context menu with your own custom context menu, this functionality is lost, and you need to write code to reenable the spell-checking feature in the context menu.</span></span> <span data-ttu-id="f2038-106">O exemplo a seguir mostra como habilitar isso em um <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f2038-106">The following example shows how to enable this on a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2038-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f2038-107">Example</span></span>  
 <span data-ttu-id="f2038-108">A exemplo a seguir mostra a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que cria um <xref:System.Windows.Controls.TextBox> com alguns eventos que são usados para implementar o menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="f2038-108">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that creates a <xref:System.Windows.Controls.TextBox> with some events that are used to implement the context menu.</span></span>  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="f2038-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f2038-109">Example</span></span>  
 <span data-ttu-id="f2038-110">O exemplo a seguir mostra o código que implementa o menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="f2038-110">The following example shows the code that implements the context menu.</span></span>  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 <span data-ttu-id="f2038-111">O código usado para fazer isso com um <xref:System.Windows.Controls.RichTextBox> é semelhante.</span><span class="sxs-lookup"><span data-stu-id="f2038-111">The code used for doing this with a <xref:System.Windows.Controls.RichTextBox> is similar.</span></span> <span data-ttu-id="f2038-112">A principal diferença está no parâmetro passado para o método `GetSpellingError`.</span><span class="sxs-lookup"><span data-stu-id="f2038-112">The main difference is in the parameter passed to the `GetSpellingError` method.</span></span> <span data-ttu-id="f2038-113">Para um <xref:System.Windows.Controls.TextBox>, passe o índice inteiro da posição do cursor:</span><span class="sxs-lookup"><span data-stu-id="f2038-113">For a <xref:System.Windows.Controls.TextBox>, pass the integer index of the caret position:</span></span>  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <span data-ttu-id="f2038-114">Para um <xref:System.Windows.Controls.RichTextBox>, passe o <xref:System.Windows.Documents.TextPointer> que especifica a posição do cursor:</span><span class="sxs-lookup"><span data-stu-id="f2038-114">For a <xref:System.Windows.Controls.RichTextBox>, pass the <xref:System.Windows.Documents.TextPointer> that specifies the caret position:</span></span>  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a><span data-ttu-id="f2038-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2038-115">See also</span></span>

- [<span data-ttu-id="f2038-116">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="f2038-116">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="f2038-117">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="f2038-117">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="f2038-118">Habilitar verificação ortográfica em um controle de edição de texto</span><span class="sxs-lookup"><span data-stu-id="f2038-118">Enable Spell Checking in a Text Editing Control</span></span>](how-to-enable-spell-checking-in-a-text-editing-control.md)
- [<span data-ttu-id="f2038-119">Usar um menu de contexto personalizado com um TextBox</span><span class="sxs-lookup"><span data-stu-id="f2038-119">Use a Custom Context Menu with a TextBox</span></span>](how-to-use-a-custom-context-menu-with-a-textbox.md)
