---
title: Como buscar um storyboard
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
ms.openlocfilehash: 656a5cb38461f71698a312e6382a3a9c29158cc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560261"
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="7b0a7-102">Como buscar um storyboard</span><span class="sxs-lookup"><span data-stu-id="7b0a7-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="7b0a7-103">O exemplo a seguir mostra como usar o <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> método de um <xref:System.Windows.Media.Animation.Storyboard> para ir para qualquer posição em uma animação de storyboard.</span><span class="sxs-lookup"><span data-stu-id="7b0a7-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b0a7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b0a7-104">Example</span></span>  
 <span data-ttu-id="7b0a7-105">Abaixo está a marcação XAML para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="7b0a7-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="7b0a7-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b0a7-106">Example</span></span>  
 <span data-ttu-id="7b0a7-107">Abaixo está o código usado junto com o XAML acima.</span><span class="sxs-lookup"><span data-stu-id="7b0a7-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7b0a7-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b0a7-108">See Also</span></span>  
 [<span data-ttu-id="7b0a7-109">Buscar um storyboard de forma síncrona</span><span class="sxs-lookup"><span data-stu-id="7b0a7-109">Seek a Storyboard Synchronously</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)
