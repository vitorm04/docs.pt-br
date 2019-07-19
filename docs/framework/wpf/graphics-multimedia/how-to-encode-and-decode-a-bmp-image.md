---
title: 'Como: Codificar e decodificar uma imagem BMP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding BMP images [WPF]
- BMP encoding [WPF]
- decoding BMP images [WPF]
- encoding image formats [WPF]
- BMP decoding [WPF]
- decoding image formats [WPF]
ms.assetid: feb5ef27-28ac-40ab-bfc2-e0456990d32c
ms.openlocfilehash: 7d3520a1b1913fe68fedb0ea9d76cc138ed661c4
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331721"
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a>Como: Codificar e decodificar uma imagem BMP
Os exemplos a seguir mostram como decodificar e codificar uma imagem bitmap (BMP) usando os <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> objetos <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> e específicos.  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como decodificar uma imagem BMP usando um <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> de a <xref:System.Uri>.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como codificar um <xref:System.Windows.Media.Imaging.BitmapSource> em uma imagem BMP usando um. <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da geração de imagens](imaging-overview.md)
