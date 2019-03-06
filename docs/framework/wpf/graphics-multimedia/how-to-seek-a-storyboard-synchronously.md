---
title: 'Como: Buscar um storyboard de forma síncrona'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- seeking Storyboards synchronously [WPF]
- Storyboards [WPF], seeking synchronously
ms.assetid: 03e06271-a946-4810-88ea-3fb4cfa9e0f1
ms.openlocfilehash: 8ac55346ac83ee94318de90655bde6053ef20687
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371314"
---
# <a name="how-to-seek-a-storyboard-synchronously"></a><span data-ttu-id="9a9b5-102">Como: Buscar um storyboard de forma síncrona</span><span class="sxs-lookup"><span data-stu-id="9a9b5-102">How to: Seek a Storyboard Synchronously</span></span>
<span data-ttu-id="9a9b5-103">O exemplo a seguir mostra como usar o <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> método de um <xref:System.Windows.Media.Animation.Storyboard> para buscar qualquer posição em uma animação de storyboard de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="9a9b5-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to seek to any position in a storyboard animation synchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a9b5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a9b5-104">Example</span></span>  
 <span data-ttu-id="9a9b5-105">A seguir está a marcação XAML para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="9a9b5-105">The following is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardSynchronouslyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml#seekstoryboardsynchronouslyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="9a9b5-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a9b5-106">Example</span></span>  
 <span data-ttu-id="9a9b5-107">Este é o código usado com o código XAML acima.</span><span class="sxs-lookup"><span data-stu-id="9a9b5-107">The following is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml.cs#seekstoryboardsynchronouslycodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardSynchronouslyExample.xaml.vb#seekstoryboardsynchronouslycodebehindexamplewholepage)]
