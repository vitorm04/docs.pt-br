---
title: 'Como: Codificar e decodificar uma imagem JPEG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding image formats [WPF]
- decoding JPEG images [WPF]
- encoding JPEG images [WPF]
- decoding image formats [WPF]
- JPEG decoding [WPF]
- JPEG encoding [WPF]
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
ms.openlocfilehash: db42411f71e2934f3e5f86a06f434da220f1882e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603502"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="308d0-102">Como: Codificar e decodificar uma imagem JPEG</span><span class="sxs-lookup"><span data-stu-id="308d0-102">How to: Encode and decode a JPEG image</span></span>

<span data-ttu-id="308d0-103">Os exemplos a seguir mostram como decodificar e codificar uma imagem JPEG usando específico <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> e <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objetos.</span><span class="sxs-lookup"><span data-stu-id="308d0-103">The following examples show how to decode and encode a JPEG image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example---decode-a-jpeg-image"></a><span data-ttu-id="308d0-104">Exemplo - decodificar uma imagem JPEG</span><span class="sxs-lookup"><span data-stu-id="308d0-104">Example - Decode a JPEG image</span></span>

<span data-ttu-id="308d0-105">Este exemplo demonstra como decodificar uma imagem JPEG usando um <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> de um <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="308d0-105">This example demonstrates how to decode a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a><span data-ttu-id="308d0-106">Exemplo – codificar uma imagem JPEG</span><span class="sxs-lookup"><span data-stu-id="308d0-106">Example - Encode a JPEG image</span></span>

<span data-ttu-id="308d0-107">Este exemplo demonstra como codificar um <xref:System.Windows.Media.Imaging.BitmapSource> imagem para JPEG usando um <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="308d0-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="308d0-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="308d0-108">See also</span></span>

- [<span data-ttu-id="308d0-109">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="308d0-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
