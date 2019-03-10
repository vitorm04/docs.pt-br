---
title: Usando codecs de imagem no GDI+ gerenciado
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: bf0d3a64ce8860d67f0dcfd37c780f03fbd7471a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713246"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Usando codecs de imagem no GDI+ gerenciado
O <xref:System.Drawing> namespace fornece a <xref:System.Drawing.Image> e <xref:System.Drawing.Bitmap> classes para armazenar e manipular imagens. Ao usar codificadores de imagem no [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode gravar imagens da memória no disco. Ao usar codificadores de imagem no [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode carregar imagens do disco na memória. Um codificador converte os dados em um <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> objeto em um formato de arquivo de disco designado. Um decodificador converte os dados em um arquivo de disco para o formato exigido pelo <xref:System.Drawing.Image> e <xref:System.Drawing.Bitmap> objetos.  
  
 O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tem codecs internos que oferecem suporte aos seguintes tipos de arquivo:  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] também tem decodificadores internos que oferecem suporte aos seguintes tipos de arquivo:  
  
-   WMF  
  
-   EMF  
  
-   ICON  
  
 Os tópicos a seguir abordam os codificadores e decodificadores mais detalhadamente:  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Listar os codificadores instalados](how-to-list-installed-encoders.md)  
 Descreve como listar os codificadores disponíveis em um computador.  
  
 [Como: Listar os decodificadores instalados](how-to-list-installed-decoders.md)  
 Descreve como listar os decodificadores disponíveis em um computador.  
  
 [Como: Determinar os parâmetros com suporte em um codificador](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Descreve como listar o <xref:System.Drawing.Imaging.EncoderParameters> compatíveis com um codificador.  
  
 [Como: Converter uma imagem BMP em uma imagem PNG](how-to-convert-a-bmp-image-to-a-png-image.md)  
 Descreve como salvar uma imagem em um formato de imagem diferente.  
  
 [Como: Definir a nível de compactação de JPEG](how-to-set-jpeg-compression-level.md)  
 Descreve como alterar o nível de qualidade de uma imagem.  
  
## <a name="reference"></a>Referência  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Sobre o Código Gerenciado no GDI+](about-gdi-managed-code.md)  
  
 [Imagens, bitmaps e metarquivos](images-bitmaps-and-metafiles.md)
