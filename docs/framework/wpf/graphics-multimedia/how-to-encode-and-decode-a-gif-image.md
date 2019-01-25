---
title: 'Como: Codificar e decodificar uma imagem GIF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding GIF images [WPF]
- encoding image formats [WPF]
- decoding GIF images [WPF]
- decoding image formats [WPF]
- GIF decoding [WPF]
- GIF encoding [WPF]
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
ms.openlocfilehash: 9b13ac8021b6f2d25209a89ff2ff9b4bb7531ad3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562460"
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="01d5f-102">Como: Codificar e decodificar uma imagem GIF</span><span class="sxs-lookup"><span data-stu-id="01d5f-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="01d5f-103">Os exemplos a seguir mostram como decodificar e codificar uma [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] usando o específico de imagem <xref:System.Windows.Media.Imaging.GifBitmapDecoder> e <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objetos.</span><span class="sxs-lookup"><span data-stu-id="01d5f-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d5f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="01d5f-104">Example</span></span>  
 <span data-ttu-id="01d5f-105">Este exemplo demonstra como decodificar uma [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] imagem usando uma <xref:System.Windows.Media.Imaging.GifBitmapDecoder> de um <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="01d5f-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="01d5f-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="01d5f-106">Example</span></span>  
 <span data-ttu-id="01d5f-107">Este exemplo demonstra como codificar um <xref:System.Windows.Media.Imaging.BitmapSource> em um [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] imagem usando uma <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="01d5f-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="01d5f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01d5f-108">See also</span></span>
- [<span data-ttu-id="01d5f-109">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="01d5f-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
