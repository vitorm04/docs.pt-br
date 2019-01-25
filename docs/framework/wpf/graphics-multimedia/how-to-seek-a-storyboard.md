---
title: 'Como: Buscar um storyboard'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
ms.openlocfilehash: 440b2dd157b56a1616f7137b1e311cb981b33861
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604451"
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="2bfad-102">Como: Buscar um storyboard</span><span class="sxs-lookup"><span data-stu-id="2bfad-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="2bfad-103">O exemplo a seguir mostra como usar o <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> método de um <xref:System.Windows.Media.Animation.Storyboard> para saltar para qualquer posição em uma animação de storyboard.</span><span class="sxs-lookup"><span data-stu-id="2bfad-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bfad-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2bfad-104">Example</span></span>  
 <span data-ttu-id="2bfad-105">Abaixo está a marcação XAML para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2bfad-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="2bfad-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2bfad-106">Example</span></span>  
 <span data-ttu-id="2bfad-107">Abaixo está o código usado com o código XAML acima.</span><span class="sxs-lookup"><span data-stu-id="2bfad-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2bfad-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bfad-108">See also</span></span>
- [<span data-ttu-id="2bfad-109">Buscar um storyboard de forma síncrona</span><span class="sxs-lookup"><span data-stu-id="2bfad-109">Seek a Storyboard Synchronously</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)
