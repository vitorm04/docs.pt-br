---
title: Usando fontes e texto
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505112"
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="1c8d0-102">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="1c8d0-102">Using Fonts and Text</span></span>
<span data-ttu-id="1c8d0-103">Há diversas classes oferecidas por GDI+ e GDI para desenhar texto em formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-103">There are several classes offered by GDI+ and GDI for drawing text on Windows Forms.</span></span> <span data-ttu-id="1c8d0-104">O GDI+ <xref:System.Drawing.Graphics> classe tem várias <xref:System.Drawing.Graphics.DrawString%2A> métodos que permitem que você especifique vários recursos de texto, como local, delimitadora retângulo, fonte e formato.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-104">The GDI+ <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="1c8d0-105">Além disso, você pode desenhar e medir texto com GDI usando estático <xref:System.Windows.Forms.TextRenderer.DrawText%2A> e <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> métodos oferecidos pelo `TextRenderer` classe.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-105">In addition, you can draw and measure text with GDI using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="1c8d0-106">Os métodos GDI também permitem que você especifique a localização, fonte e formato.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-106">The GDI methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="1c8d0-107">Você pode escolher GDI ou GDI+ para renderização de texto; No entanto, a GDI geralmente oferece um melhor desempenho e medição de texto mais precisa.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-107">You can choose either GDI or GDI+ for text rendering; however, GDI generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="1c8d0-108">Outras classes que contribuem para renderização de texto incluem `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, e `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c8d0-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1c8d0-109">In This Section</span></span>  
 [<span data-ttu-id="1c8d0-110">Como: Construir fontes e famílias de fontes</span><span class="sxs-lookup"><span data-stu-id="1c8d0-110">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="1c8d0-111">Mostra como criar objetos `Font` e `FontFamily`.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="1c8d0-112">Como: Desenhar texto em um local especificado</span><span class="sxs-lookup"><span data-stu-id="1c8d0-112">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="1c8d0-113">Descreve como desenhar texto em um determinado local usando GDI+ e GDI.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-113">Describes how to draw text in a certain location using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="1c8d0-114">Como: Desenhar texto encapsulado em um retângulo</span><span class="sxs-lookup"><span data-stu-id="1c8d0-114">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="1c8d0-115">Explica como desenhar texto em um retângulo usando GDI+ e GDI.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-115">Explains how to draw text in a rectangle using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="1c8d0-116">Como: Desenhar texto com GDI</span><span class="sxs-lookup"><span data-stu-id="1c8d0-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="1c8d0-117">Demonstra como usar GDI para desenhar texto.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-117">Demonstrates how to use GDI for drawing text.</span></span>  
  
 [<span data-ttu-id="1c8d0-118">Como: Alinhar um texto desenhado</span><span class="sxs-lookup"><span data-stu-id="1c8d0-118">How to: Align Drawn Text</span></span>](how-to-align-drawn-text.md)  
 <span data-ttu-id="1c8d0-119">Mostra como formatar texto GDI+ e GDI.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-119">Shows how to format GDI+ and GDI text.</span></span>  
  
 [<span data-ttu-id="1c8d0-120">Como: Criar texto Vertical</span><span class="sxs-lookup"><span data-stu-id="1c8d0-120">How to: Create Vertical Text</span></span>](how-to-create-vertical-text.md)  
 <span data-ttu-id="1c8d0-121">Descreve como desenhar texto alinhado verticalmente com o GDI+.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-121">Describes how to draw vertically aligned text with GDI+.</span></span>  
  
 [<span data-ttu-id="1c8d0-122">Como: Definir paradas de tabulação em um texto desenhado</span><span class="sxs-lookup"><span data-stu-id="1c8d0-122">How to: Set Tab Stops in Drawn Text</span></span>](how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="1c8d0-123">Mostra como desenhar textos com paradas de tabulação com o GDI+.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-123">Shows how draw text with tab stops with GDI+.</span></span>  
  
 [<span data-ttu-id="1c8d0-124">Como: Enumerar as fontes instaladas</span><span class="sxs-lookup"><span data-stu-id="1c8d0-124">How to: Enumerate Installed Fonts</span></span>](how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="1c8d0-125">Explica como listar os nomes das fontes instaladas.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="1c8d0-126">Como: Criar uma coleção de fontes privada</span><span class="sxs-lookup"><span data-stu-id="1c8d0-126">How to: Create a Private Font Collection</span></span>](how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="1c8d0-127">Descreve como criar um <xref:System.Drawing.Text.PrivateFontCollection> objeto.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="1c8d0-128">Como: Obter métricas de fontes</span><span class="sxs-lookup"><span data-stu-id="1c8d0-128">How to: Obtain Font Metrics</span></span>](how-to-obtain-font-metrics.md)  
 <span data-ttu-id="1c8d0-129">Mostra como obter métricas de fonte, como subida e descida de células.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="1c8d0-130">Como: Usar suavização com texto</span><span class="sxs-lookup"><span data-stu-id="1c8d0-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="1c8d0-131">Explica como usar a suavização ao desenhar texto.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1c8d0-132">Referência</span><span class="sxs-lookup"><span data-stu-id="1c8d0-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="1c8d0-133">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="1c8d0-134">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="1c8d0-135">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="1c8d0-136">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="1c8d0-137">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c8d0-137">Describes this class and contains links to all of its members.</span></span>
