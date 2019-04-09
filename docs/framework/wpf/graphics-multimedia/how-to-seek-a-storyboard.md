---
title: 'Como: Buscar um Storyboard'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
ms.openlocfilehash: a57272c17a5bc6f5baaa21fb77233fc5693d1914
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131658"
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="dfbf2-102">Como: Buscar um Storyboard</span><span class="sxs-lookup"><span data-stu-id="dfbf2-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="dfbf2-103">O exemplo a seguir mostra como usar o <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> método de um <xref:System.Windows.Media.Animation.Storyboard> para saltar para qualquer posição em uma animação de storyboard.</span><span class="sxs-lookup"><span data-stu-id="dfbf2-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfbf2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfbf2-104">Example</span></span>  
 <span data-ttu-id="dfbf2-105">Abaixo está a marcação XAML para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="dfbf2-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="dfbf2-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfbf2-106">Example</span></span>  
 <span data-ttu-id="dfbf2-107">Abaixo está o código usado com o código XAML acima.</span><span class="sxs-lookup"><span data-stu-id="dfbf2-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="dfbf2-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfbf2-108">See also</span></span>

- [<span data-ttu-id="dfbf2-109">Buscar um Storyboard de forma síncrona</span><span class="sxs-lookup"><span data-stu-id="dfbf2-109">Seek a Storyboard Synchronously</span></span>](how-to-seek-a-storyboard-synchronously.md)
