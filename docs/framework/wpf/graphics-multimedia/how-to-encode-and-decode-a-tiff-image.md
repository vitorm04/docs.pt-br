---
title: 'Como: Codificar e decodificar uma imagem TIFF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TIFF encoding [WPF]
- encoding TIFF images [WPF]
- encoding image formats [WPF]
- decoding TIFF images [WPF]
- decoding image formats [WPF]
- TIFF decoding [WPF]
ms.assetid: 1dfe3209-fc73-40e6-ad1c-71c1c58b3364
ms.openlocfilehash: e89f39dedcc210aaa6917b4b964d1944673047b5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356670"
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a>Como: Codificar e decodificar uma imagem TIFF
Os exemplos a seguir mostram como decodificar e codificar uma [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] usando o específico de imagem <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> e <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objetos.  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como decodificar uma [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] imagem usando uma <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> de um <xref:System.Uri>.  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como codificar um <xref:System.Windows.Media.Imaging.BitmapSource> em um [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] imagem usando uma <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da geração de imagens](imaging-overview.md)
