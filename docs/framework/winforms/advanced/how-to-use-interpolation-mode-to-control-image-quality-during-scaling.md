---
title: "Como usar o modo de interpolação para controlar a qualidade da imagem durante o dimensionamento"
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
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10a0ef4e7fd8514245a7659dd515d8f363a716ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>Como usar o modo de interpolação para controlar a qualidade da imagem durante o dimensionamento
O modo de interpolação de um <xref:System.Drawing.Graphics> objeto influencia a maneira [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imagens escalas (expande e reduz o tempo). O <xref:System.Drawing.Drawing2D.InterpolationMode> enumeração define os vários modos de interpolação, alguns dos quais são mostrados na lista a seguir:  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 Para alongar uma imagem, cada pixel da imagem original deve ser mapeado para um grupo de pixels da imagem maior. Para encolher uma imagem, cada pixel da imagem original deve ser mapeado para pixels únicos da imagem menor. A eficácia dos algoritmos que executam esses mapeamentos determina a qualidade de uma imagem dimensionada. Algoritmos que produzem imagens dimensionadas de qualidade superior tendem a exigir mais tempo de processamento. Na lista anterior, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> é o modo de qualidade inferior e <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> é o modo mais alta qualidade.  
  
 Para definir o modo de interpolação, atribua um dos membros a <xref:System.Drawing.Drawing2D.InterpolationMode> enumeração para o <xref:System.Drawing.Graphics.InterpolationMode%2A> propriedade de um <xref:System.Drawing.Graphics> objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha uma imagem e, em seguida, reduz a imagem com três modos diferentes de interpolação.  
  
 A ilustração a seguir mostra a imagem original e as três imagens menores.  
  
 ![Imagem com configurações de interpolação variadas](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Imagens, bitmaps e metarquivos](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
