---
title: Como encadear objetos BitmapSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BitmapSource objects [WPF], chaining
- graphics [WPF], chaining BitmapSource objects
- chaining BitmapSource objects [WPF]
ms.assetid: 32d88853-395b-4855-9685-51a482a3b421
ms.openlocfilehash: 5c70b6ec132234959404203fb62567ddb0acf762
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558859"
---
# <a name="how-to-chain-bitmapsource-objects-together"></a><span data-ttu-id="fdbfb-102">Como encadear objetos BitmapSource</span><span class="sxs-lookup"><span data-stu-id="fdbfb-102">How to: Chain BitmapSource Objects Together</span></span>
<span data-ttu-id="fdbfb-103">Este exemplo mostra como você pode aplicar uma variedade de efeitos em uma fonte de imagem ao encadear vários <xref:System.Windows.Media.Imaging.BitmapSource> objetos derivados.</span><span class="sxs-lookup"><span data-stu-id="fdbfb-103">This example shows how you can apply a variety of effects to an image source by chaining multiple <xref:System.Windows.Media.Imaging.BitmapSource> derived objects together.</span></span>  
  
 <span data-ttu-id="fdbfb-104">O exemplo a seguir usa encadeamento para inverter e alterar o formato de pixel da origem de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="fdbfb-104">The following example uses chaining to flip and change the pixel format of the source of an image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdbfb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fdbfb-105">Example</span></span>  
 [!code-xaml[ImagingSnippetGallery_snip#ChainedBitmapSourcesXamlExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_snip/CS/ChainedBitmapSourcesExample.xaml#chainedbitmapsourcesxamlexamplewholepage)]  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/ChainedBitmapSourcesExample.cs#chainedbitmapsourcescodeexamplewholepage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/ChainedBitmapSourcesExample.vb#chainedbitmapsourcescodeexamplewholepage)]
