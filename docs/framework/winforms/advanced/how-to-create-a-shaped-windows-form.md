---
title: 'Como: Criar um formulário do Windows moldado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], rounded
- Windows Forms, custom shapes
- Windows Forms, shaped
- shaped forms
- forms [Windows Forms], changing the shape of
- forms [Windows Forms], circular
- forms [Windows Forms], nonrectangular
- Windows Forms, nonrectangular shape
- Windows Forms, rounded
- Windows Forms, circular
- forms [Windows Forms], custom shapes
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
ms.openlocfilehash: 937b785078e58026a5360155805f9cf37031cec6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527270"
---
# <a name="how-to-create-a-shaped-windows-form"></a><span data-ttu-id="207db-102">Como: Criar um formulário do Windows moldado</span><span class="sxs-lookup"><span data-stu-id="207db-102">How to: Create a Shaped Windows Form</span></span>
<span data-ttu-id="207db-103">Este exemplo fornece um formulário de uma forma elíptica que redimensiona com o formulário.</span><span class="sxs-lookup"><span data-stu-id="207db-103">This example gives a form an elliptical shape that resizes with the form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="207db-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="207db-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="207db-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="207db-105">Compiling the Code</span></span>  
 <span data-ttu-id="207db-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="207db-106">This example requires:</span></span>  
  
-   <span data-ttu-id="207db-107">Referências aos namespaces <xref:System.Windows.Forms> e <xref:System.Drawing>.</span><span class="sxs-lookup"><span data-stu-id="207db-107">References to the <xref:System.Windows.Forms> and <xref:System.Drawing> namespaces.</span></span>  
  
 <span data-ttu-id="207db-108">Este exemplo substitui o <xref:System.Windows.Forms.Control.OnPaint%2A> método para alterar a forma do formulário.</span><span class="sxs-lookup"><span data-stu-id="207db-108">This example overrides the <xref:System.Windows.Forms.Control.OnPaint%2A> method to change the shape of the form.</span></span> <span data-ttu-id="207db-109">Para usar esse código, copie a declaração do método, bem como o código de desenho dentro do método.</span><span class="sxs-lookup"><span data-stu-id="207db-109">To use this code, copy the method declaration as well as the drawing code inside the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="207db-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="207db-110">See also</span></span>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Region>
- <xref:System.Drawing>
- <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>
- <xref:System.Windows.Forms.Control.Region%2A>
- [<span data-ttu-id="207db-111">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="207db-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
