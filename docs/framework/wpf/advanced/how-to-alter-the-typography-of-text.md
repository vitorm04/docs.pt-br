---
title: Como alterar a tipografia de texto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
ms.openlocfilehash: fcc9c894970934bb5a69debef2f4e38297f82198
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542923"
---
# <a name="how-to-alter-the-typography-of-text"></a><span data-ttu-id="d710b-102">Como alterar a tipografia de texto</span><span class="sxs-lookup"><span data-stu-id="d710b-102">How-to: Alter the Typography of Text</span></span>
<span data-ttu-id="d710b-103">O exemplo a seguir mostra como definir o <xref:System.Windows.Documents.TextElement.Typography%2A> de atributo, usando <xref:System.Windows.Documents.Paragraph> como o elemento de exemplo.</span><span class="sxs-lookup"><span data-stu-id="d710b-103">The following example shows how to set the <xref:System.Windows.Documents.TextElement.Typography%2A> attribute, using <xref:System.Windows.Documents.Paragraph> as the example element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d710b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d710b-104">Example</span></span>  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 <span data-ttu-id="d710b-105">A figura a seguir mostra como esse exemplo é renderizado.</span><span class="sxs-lookup"><span data-stu-id="d710b-105">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="d710b-106">![Captura de tela: texto com tipografia alterada](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")</span><span class="sxs-lookup"><span data-stu-id="d710b-106">![Screenshot: Text with altered typography](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")</span></span>  
  
 <span data-ttu-id="d710b-107">Em comparação, a figura a seguir mostra como um exemplo semelhante com propriedades tipográficas padrão é renderizado.</span><span class="sxs-lookup"><span data-stu-id="d710b-107">In contrast, the following figure shows how a similar example with default typographic properties renders.</span></span>  
  
 <span data-ttu-id="d710b-108">![Captura de tela: texto com tipografia alterada](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")</span><span class="sxs-lookup"><span data-stu-id="d710b-108">![Screenshot: Text with altered typography](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")</span></span>  
  
## <a name="example"></a><span data-ttu-id="d710b-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d710b-109">Example</span></span>  
 <span data-ttu-id="d710b-110">O exemplo a seguir mostra como definir o <xref:System.Windows.Controls.TextBox.Typography%2A> propriedade programaticamente.</span><span class="sxs-lookup"><span data-stu-id="d710b-110">The following example shows how to set the <xref:System.Windows.Controls.TextBox.Typography%2A> property programmatically.</span></span>  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a><span data-ttu-id="d710b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d710b-111">See Also</span></span>  
 [<span data-ttu-id="d710b-112">Visão geral do documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="d710b-112">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
