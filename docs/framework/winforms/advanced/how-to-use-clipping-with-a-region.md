---
title: "Como usar recorte com uma região"
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
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b57ffa91a41900e10aa921bd42509b1288134ff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-clipping-with-a-region"></a>Como usar recorte com uma região
Uma das propriedades do <xref:System.Drawing.Graphics> classe é a região de recorte. Todos os desenhos feito por um determinado <xref:System.Drawing.Graphics> objeto é restrito à região de clip que <xref:System.Drawing.Graphics> objeto. Você pode definir a região de clip chamando o <xref:System.Drawing.Graphics.SetClip%2A> método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir constrói um caminho que consiste em um único polígono. Em seguida, o código constrói uma região, com base no caminho. A região é passada para o <xref:System.Drawing.Graphics.SetClip%2A> método de um <xref:System.Drawing.Graphics> objeto e, em seguida, duas cadeias de caracteres são desenhadas.  
  
 A ilustração a seguir mostra as cadeias de caracteres recortadas.  
  
 ![Recortar](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também  
 [Regiões no GDI+](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Usando regiões](../../../../docs/framework/winforms/advanced/using-regions.md)
