---
title: Como codificar e decodificar uma imagem PNG
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- PNG encoding [WPF]
- decoding PNG images [WPF]
- PNG decoding [WPF]
- encoding image formats [WPF]
- decoding image formats [WPF]
- encoding PNG images [WPF]
ms.assetid: 3d31d186-af73-47f0-b5a7-c26ae46409a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fa304515e508fab246a6946c5a8026369cda250
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-and-decode-a-png-image"></a>Como codificar e decodificar uma imagem PNG
Os exemplos a seguir mostram como decodificar e codificar um [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] imagem usando específico <xref:System.Windows.Media.Imaging.PngBitmapDecoder> e <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objetos.  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como decodificar uma [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] imagem usando uma <xref:System.Windows.Media.Imaging.PngBitmapDecoder> de um <xref:System.IO.FileStream>.  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como codificar um <xref:System.Windows.Media.Imaging.BitmapSource> em uma [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] imagem usando um <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da geração de imagens](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
