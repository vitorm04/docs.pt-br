---
title: 'Como: Encadear objetos BitmapSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BitmapSource objects [WPF], chaining
- graphics [WPF], chaining BitmapSource objects
- chaining BitmapSource objects [WPF]
ms.assetid: 32d88853-395b-4855-9685-51a482a3b421
ms.openlocfilehash: 403a2a8683e65fd71df89befd59744ac3fe6200c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785652"
---
# <a name="how-to-chain-bitmapsource-objects-together"></a><span data-ttu-id="00c5c-102">Como: Encadear objetos BitmapSource</span><span class="sxs-lookup"><span data-stu-id="00c5c-102">How to: Chain BitmapSource Objects Together</span></span>
<span data-ttu-id="00c5c-103">Este exemplo mostra como você pode aplicar uma variedade de efeitos em uma fonte de imagem ao encadear vários <xref:System.Windows.Media.Imaging.BitmapSource> objetos derivados.</span><span class="sxs-lookup"><span data-stu-id="00c5c-103">This example shows how you can apply a variety of effects to an image source by chaining multiple <xref:System.Windows.Media.Imaging.BitmapSource> derived objects together.</span></span>  
  
 <span data-ttu-id="00c5c-104">O exemplo a seguir usa o encadeamento para inverter e alterar o formato de pixel da origem de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="00c5c-104">The following example uses chaining to flip and change the pixel format of the source of an image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00c5c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00c5c-105">Example</span></span>  
 [!code-xaml[ImagingSnippetGallery_snip#ChainedBitmapSourcesXamlExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_snip/CS/ChainedBitmapSourcesExample.xaml#chainedbitmapsourcesxamlexamplewholepage)]  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/ChainedBitmapSourcesExample.cs#chainedbitmapsourcescodeexamplewholepage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/ChainedBitmapSourcesExample.vb#chainedbitmapsourcescodeexamplewholepage)]
