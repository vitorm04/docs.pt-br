---
title: 'Como: Alterar a tipografia de texto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
ms.openlocfilehash: 4c027424632f8671ba8d7cae1c899ef3a53edc26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078857"
---
# <a name="how-to-alter-the-typography-of-text"></a><span data-ttu-id="bae32-102">Como: Alterar a tipografia de texto</span><span class="sxs-lookup"><span data-stu-id="bae32-102">How-to: Alter the Typography of Text</span></span>
<span data-ttu-id="bae32-103">O exemplo a seguir mostra como definir a <xref:System.Windows.Documents.TextElement.Typography%2A> de atributo, usando <xref:System.Windows.Documents.Paragraph> como o elemento de exemplo.</span><span class="sxs-lookup"><span data-stu-id="bae32-103">The following example shows how to set the <xref:System.Windows.Documents.TextElement.Typography%2A> attribute, using <xref:System.Windows.Documents.Paragraph> as the example element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bae32-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bae32-104">Example</span></span>  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 <span data-ttu-id="bae32-105">A figura a seguir mostra como esse exemplo é renderizado.</span><span class="sxs-lookup"><span data-stu-id="bae32-105">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="bae32-106">![Captura de tela: Texto com tipografia alterada](./media/textelement-typog.png "TextElement_Typog")</span><span class="sxs-lookup"><span data-stu-id="bae32-106">![Screenshot: Text with altered typography](./media/textelement-typog.png "TextElement_Typog")</span></span>  
  
 <span data-ttu-id="bae32-107">Em comparação, a figura a seguir mostra como um exemplo semelhante com propriedades tipográficas padrão é renderizado.</span><span class="sxs-lookup"><span data-stu-id="bae32-107">In contrast, the following figure shows how a similar example with default typographic properties renders.</span></span>  
  
 <span data-ttu-id="bae32-108">![Captura de tela: Texto com tipografia alterada](./media/textelement-typog-default.png "TextElement_Typog_Default")</span><span class="sxs-lookup"><span data-stu-id="bae32-108">![Screenshot: Text with altered typography](./media/textelement-typog-default.png "TextElement_Typog_Default")</span></span>  
  
## <a name="example"></a><span data-ttu-id="bae32-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bae32-109">Example</span></span>  
 <span data-ttu-id="bae32-110">O exemplo a seguir mostra como definir o <xref:System.Windows.Controls.TextBox.Typography%2A> propriedade programaticamente.</span><span class="sxs-lookup"><span data-stu-id="bae32-110">The following example shows how to set the <xref:System.Windows.Controls.TextBox.Typography%2A> property programmatically.</span></span>  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a><span data-ttu-id="bae32-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bae32-111">See also</span></span>

- [<span data-ttu-id="bae32-112">Visão geral do documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="bae32-112">Flow Document Overview</span></span>](flow-document-overview.md)
