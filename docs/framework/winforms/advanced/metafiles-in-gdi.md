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
ms.openlocfilehash: bb972f158496192aa38f10564209bb2781837414
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119854"
---
# <a name="metafiles-in-gdi"></a>Metarquivos no GDI+
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece o <xref:System.Drawing.Imaging.Metafile> de classe para que você pode registrar e exibir metarquivos. Um metarquivo, também chamado de uma imagem de vetor, é uma imagem que é armazenada como uma sequência de comandos e configurações de desenho. Os comandos e configurações registrados em um <xref:System.Drawing.Imaging.Metafile> objeto pode ser armazenado na memória ou salvos em um arquivo ou fluxo.  
  
## <a name="metafile-formats"></a>Formatos de metarquivos  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pode exibir metarquivos que foram armazenados nos seguintes formatos:  
  
-   Metarquivo do Windows (WMF)  
  
-   EMF (Metarquivo Avançado)  
  
-   EMF+  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pode registrar metarquivos nos formatos EMF e EMF +, mas não no formato WMF.  
  
 EMF+ é uma extensão de EMF que permite que registros [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sejam armazenados. Há duas variações no formato EMF +: EMF + somente e EMF + duplo. Metarquivos Apenas EMF+ contêm apenas registros [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Esses metarquivos podem ser exibidos por [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], mas não por [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]. Metarquivos EMF+ Duplos contêm registros [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]. Cada registro [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] em um metarquivo EMF+ Duplo é associado a um registro [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] alternativo. Esses metarquivos podem ser exibidos por [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ou por [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 O exemplo a seguir exibe um metarquivo que foi salvo anteriormente como um arquivo. O metarquivo é exibido com seu canto superior esquerdo em (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Consulte também

- [Imagens, bitmaps e metarquivos](images-bitmaps-and-metafiles.md)
