---
title: 'Como: Habilitar filtragem de texto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimming text
- trimming text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 25fff566868e792004a915fee195485c4a1f385f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474131"
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="59e5e-102">Como: Habilitar filtragem de texto</span><span class="sxs-lookup"><span data-stu-id="59e5e-102">How to: Enable Text Trimming</span></span>

<span data-ttu-id="59e5e-103">Este exemplo demonstra o uso e efeitos dos valores disponíveis no <xref:System.Windows.TextTrimming> enumeração.</span><span class="sxs-lookup"><span data-stu-id="59e5e-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>

## <a name="example"></a><span data-ttu-id="59e5e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59e5e-104">Example</span></span>

<span data-ttu-id="59e5e-105">O exemplo a seguir define uma <xref:System.Windows.Controls.TextBlock> elemento com o <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> conjunto de atributos.</span><span class="sxs-lookup"><span data-stu-id="59e5e-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>

[!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]

<span data-ttu-id="59e5e-106">Configuração correspondente <xref:System.Windows.TextTrimming> propriedade no código é demonstrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="59e5e-106">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>

[!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
[!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]

<span data-ttu-id="59e5e-107">Existem atualmente três opções para cortar texto: **CharacterEllipsis**, **WordEllipsis**, e **None**.</span><span class="sxs-lookup"><span data-stu-id="59e5e-107">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>

<span data-ttu-id="59e5e-108">Quando <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> é definido como **CharacterEllipsis**, texto é cortado e continuado com uma elipse no caractere mais próximo à borda de corte.</span><span class="sxs-lookup"><span data-stu-id="59e5e-108">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="59e5e-109">Essa configuração tende a cortar o texto para se ajustar mais bem ao limite de corte, mas pode resultar em palavras parcialmente cortadas.</span><span class="sxs-lookup"><span data-stu-id="59e5e-109">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="59e5e-110">A figura a seguir mostra o efeito dessa configuração em um <xref:System.Windows.Controls.TextBlock> semelhante àquele definido acima.</span><span class="sxs-lookup"><span data-stu-id="59e5e-110">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>

<span data-ttu-id="59e5e-111">![Exemplo: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="59e5e-111">![Example: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span></span>

<span data-ttu-id="59e5e-112">Quando <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> é definido como **WordEllipsis**, texto é cortado e continuado com uma elipse no final da primeira palavra completa mais próxima à borda de corte.</span><span class="sxs-lookup"><span data-stu-id="59e5e-112">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="59e5e-113">Essa configuração não mostrará palavras parcialmente cortadas, mas tende a não cortar o texto tão próximo à borda de corte quanto o **CharacterEllipsis** configuração.</span><span class="sxs-lookup"><span data-stu-id="59e5e-113">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="59e5e-114">A figura a seguir mostra o efeito dessa configuração no <xref:System.Windows.Controls.TextBlock> definido acima.</span><span class="sxs-lookup"><span data-stu-id="59e5e-114">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>

<span data-ttu-id="59e5e-115">![Exemplo: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="59e5e-115">![Example: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span></span>

<span data-ttu-id="59e5e-116">Quando <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> é definido como **None**, nenhuma quebra de texto é realizada.</span><span class="sxs-lookup"><span data-stu-id="59e5e-116">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="59e5e-117">Nesse caso, o texto é simplesmente recortado para o limite do contêiner de texto pai.</span><span class="sxs-lookup"><span data-stu-id="59e5e-117">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="59e5e-118">A figura a seguir mostra o efeito dessa configuração em um <xref:System.Windows.Controls.TextBlock> semelhante àquele definido acima.</span><span class="sxs-lookup"><span data-stu-id="59e5e-118">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>

<span data-ttu-id="59e5e-119">![Exemplo: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="59e5e-119">![Example: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span></span>
