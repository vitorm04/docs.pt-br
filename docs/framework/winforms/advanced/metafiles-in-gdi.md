---
title: Metarquivos no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504595"
---
# <a name="metafiles-in-gdi"></a>Metarquivos no GDI+
GDI+ fornece o <xref:System.Drawing.Imaging.Metafile> de classe para que você pode registrar e exibir metarquivos. Um metarquivo, também chamado de uma imagem de vetor, é uma imagem que é armazenada como uma sequência de comandos e configurações de desenho. Os comandos e configurações registrados em um <xref:System.Drawing.Imaging.Metafile> objeto pode ser armazenado na memória ou salvos em um arquivo ou fluxo.  
  
## <a name="metafile-formats"></a>Formatos de metarquivos  
 GDI+ pode exibir metarquivos que foram armazenados nos seguintes formatos:  
  
- Metarquivo do Windows (WMF)  
  
- EMF (Metarquivo Avançado)  
  
- EMF+  
  
 GDI+ pode registrar metarquivos nos formatos EMF e EMF +, mas não no formato WMF.  
  
 EMF + é uma extensão de EMF que permite que os registros de GDI+ a ser armazenado. Há duas variações no formato EMF +: EMF + somente e EMF + duplo. Metarquivos apenas EMF + contêm apenas registros de GDI+. Esses metarquivos podem ser exibidos por GDI+, mas não por GDI. Metarquivos EMF + duplos contêm registros GDI+ e GDI. Cada registro de GDI+ em um metarquivo EMF + duplo é emparelhado com um registro GDI alternativo. Esses metarquivos podem ser exibidos por GDI+ ou por GDI.  
  
 O exemplo a seguir exibe um metarquivo que foi salvo anteriormente como um arquivo. O metarquivo é exibido com seu canto superior esquerdo em (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Consulte também

- [Imagens, bitmaps e metarquivos](images-bitmaps-and-metafiles.md)
