---
title: Como criar um pincel sólido
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
ms.openlocfilehash: 8dad10fbfb0dfb34fee6a5640b1a49e7fb234479
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520741"
---
# <a name="how-to-create-a-solid-brush"></a>Como criar um pincel sólido
Este exemplo cria um <xref:System.Drawing.SolidBrush> objeto que pode ser usado por um <xref:System.Drawing.Graphics> objeto para preencher as formas.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Depois de terminar de usá-los, você deve chamar <xref:System.IDisposable.Dispose%2A> em objetos que consomem recursos do sistema, como objetos de pincel.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.SolidBrush>  
 <xref:System.Drawing.Brush>  
 [Introdução à Programação de Elementos Gráficos](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Pincéis e Formas Preenchidas no GDI+](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 [Usando um pincel para preencher formas](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
