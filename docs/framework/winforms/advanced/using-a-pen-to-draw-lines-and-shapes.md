---
title: Usando uma caneta para desenhar linhas e formas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0913dc2745e1b244e4b03c0e6b946441a401c5b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="1c0f2-102">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="1c0f2-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="1c0f2-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objetos para desenhar o contorno de formas, curvas e segmentos de linha.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="1c0f2-104">Nesta seção, *linha* refere-se a qualquer uma dessas opções, a menos que especificado como um segmento de linha.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="1c0f2-105">Defina as propriedades de uma caneta para controlar a cor, largura, alinhamento e o estilo das linhas desenhadas com essa caneta.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c0f2-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1c0f2-106">In This Section</span></span>  
 [<span data-ttu-id="1c0f2-107">Como Usar uma Caneta para Desenhar Linhas</span><span class="sxs-lookup"><span data-stu-id="1c0f2-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="1c0f2-108">Explica como desenhar linhas.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="1c0f2-109">Como usar uma Caneta para Desenhar Retângulos</span><span class="sxs-lookup"><span data-stu-id="1c0f2-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="1c0f2-110">Descreve como desenhar retângulos.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="1c0f2-111">Como Definir a Largura e o Alinhamento de uma Caneta</span><span class="sxs-lookup"><span data-stu-id="1c0f2-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="1c0f2-112">Explica como alterar a largura e o alinhamento de um `Pen` objeto.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="1c0f2-113">Como Desenhar uma Linha com Terminações</span><span class="sxs-lookup"><span data-stu-id="1c0f2-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="1c0f2-114">Descreve como adicionar delimitada ao desenhar uma linha.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="1c0f2-115">Como Unir Linhas</span><span class="sxs-lookup"><span data-stu-id="1c0f2-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="1c0f2-116">Mostra como unir duas linhas.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="1c0f2-117">Como Desenhar uma Linha Tracejada Personalizada</span><span class="sxs-lookup"><span data-stu-id="1c0f2-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="1c0f2-118">Descreve como desenhar uma linha tracejada.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="1c0f2-119">Como Desenhar uma Linha Preenchida com uma Textura</span><span class="sxs-lookup"><span data-stu-id="1c0f2-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="1c0f2-120">Explica como desenhar uma linha preenchida a textura.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1c0f2-121">Referência</span><span class="sxs-lookup"><span data-stu-id="1c0f2-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="1c0f2-122">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c0f2-122">Describes this class and has links to all its members.</span></span>
