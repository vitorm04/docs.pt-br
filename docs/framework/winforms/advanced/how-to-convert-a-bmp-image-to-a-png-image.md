---
title: 'Como: converter uma imagem BMP em uma imagem PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: 3072c07781a8e8e57b64b48e5b4c304c2a0a0efb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217010"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Como: converter uma imagem BMP em uma imagem PNG
Muitas vezes, convém converter do formato de arquivo de uma imagem para outra. Você pode fazer essa conversão facilmente por meio da chamada a <xref:System.Drawing.Image.Save%2A> método da <xref:System.Drawing.Image> classe e especificando o <xref:System.Drawing.Imaging.ImageFormat> para o formato de arquivo de imagem desejada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir carrega uma imagem BMP de um tipo e salva a imagem no formato PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um aplicativo Windows Forms.  
  
-   Uma referência para o `System.Drawing.Imaging` namespace.  
  
## <a name="see-also"></a>Consulte também

- [Como: listar os codificadores instalados](how-to-list-installed-encoders.md)
- [Usando codecs de imagem no GDI+ gerenciado](using-image-encoders-and-decoders-in-managed-gdi.md)
- [Tipos de bitmaps](types-of-bitmaps.md)
