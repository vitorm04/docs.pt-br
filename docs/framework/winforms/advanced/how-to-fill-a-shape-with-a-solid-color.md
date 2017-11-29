---
title: "Como preencher uma forma com uma cor sólida"
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
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb3e160392a903083386d9942f8e2cfe31ee89a4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>Como preencher uma forma com uma cor sólida
Para preencher uma forma com uma cor sólida, criar um <xref:System.Drawing.SolidBrush> do objeto e, em seguida, passar que <xref:System.Drawing.SolidBrush> objeto como um argumento para um dos métodos de preenchimento de <xref:System.Drawing.Graphics> classe. O exemplo a seguir mostra como preencher uma elipse com a cor vermelha.  
  
## <a name="example"></a>Exemplo  
 No código a seguir, o <xref:System.Drawing.SolidBrush.%23ctor%2A> construtor usa uma <xref:System.Drawing.Color> objeto como seu único argumento. Os valores usados pelo <xref:System.Drawing.Color.FromArgb%2A> método representam os componentes alfa, vermelhos, verdes e azuis da cor. Cada um desses valores deve estar no intervalo de 0 a 255. O primeiro 255 indica que a cor é totalmente opaca e o segundo 255 indica que o componente vermelho é de intensidade total. Os dois zeros indicam que os componentes verde e azul têm uma intensidade igual a 0.  
  
 Os quatro números (0, 0, 100, 60) passado para o <xref:System.Drawing.Graphics.FillEllipse%2A> método especificar o local e o tamanho do retângulo delimitador para a elipse. O retângulo tem um canto superior esquerdo de (0, 0), uma largura de 100 e uma altura de 60.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Usando um pincel para preencher formas](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
