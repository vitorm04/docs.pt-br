---
title: Como preencher uma forma com uma textura de imagem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b5ef87762b08daa973237e7b3da1068640e08bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Como preencher uma forma com uma textura de imagem
Você pode preencher uma forma fechada com uma textura usando o <xref:System.Drawing.Image> classe e o <xref:System.Drawing.TextureBrush> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir preenche uma elipse com uma imagem. O código constrói um <xref:System.Drawing.Image> de objeto e, em seguida, passa o endereço do que <xref:System.Drawing.Image> objeto como um argumento para um <xref:System.Drawing.TextureBrush.%23ctor%2A> construtor. A terceira instrução redimensiona a imagem e a quarta instrução preenche a elipse com repetidas cópias da imagem dimensionada.  
  
 No código a seguir, o <xref:System.Drawing.TextureBrush.Transform%2A> propriedade contém a transformação que é aplicada à imagem antes que ela é desenhada. Suponha que a imagem original possui uma largura de 640 pixels e uma altura de 480 pixels. A transformação reduz a imagem a 75 × 75 configurando os valores de colocação em escala horizontal e vertical.  
  
> [!NOTE]
>  No exemplo a seguir, o tamanho da imagem é 75 × 75 e o tamanho da elipse é 150 × 250. Como a imagem é menor do que a elipse que ela está preenchendo, a elipse é organizada lado a lado com a imagem. Lado a lado significa que a imagem é repetida horizontal e verticalmente até o limite da forma ser atingido. Para obter mais informações sobre o organização lado a lado, consulte [Como organizar lado a lado uma forma com uma imagem](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Usando um pincel para preencher formas](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
