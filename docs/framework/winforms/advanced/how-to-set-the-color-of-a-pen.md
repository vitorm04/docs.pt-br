---
title: Como definir a cor de uma caneta
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
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 452e88b4b41a22cc78f73e120e49468e4f4dad56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-color-of-a-pen"></a>Como definir a cor de uma caneta
Este exemplo altera a cor de um pré-existente <xref:System.Drawing.Pen> objeto  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um <xref:System.Drawing.Pen> objeto chamado `myPen`.  
  
## <a name="robust-programming"></a>Programação robusta  
 Você deve chamar <xref:System.Drawing.Pen.Dispose%2A> em objetos que consomem recursos do sistema (como <xref:System.Drawing.Pen> objetos) depois de terminar de usá-los.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Pen>  
 [Introdução à Programação de Elementos Gráficos](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Como Criar uma Caneta](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Usando uma caneta para desenhar linhas e formas](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Canetas, Linhas e Retângulos no GDI+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
