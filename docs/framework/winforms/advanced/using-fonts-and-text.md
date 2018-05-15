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
ms.openlocfilehash: d157b51e24009d847dede9ea6a9f81c8898c5b06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="1c9d6-102">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="1c9d6-102">Using Fonts and Text</span></span>
<span data-ttu-id="1c9d6-103">Há diversas classes oferecidas por [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] para desenhar textos no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="1c9d6-104">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> classe tem várias <xref:System.Drawing.Graphics.DrawString%2A> métodos que permitem que você especifique vários recursos de texto, como local, delimitadora retângulo, fonte e formato.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="1c9d6-105">Além disso, você pode desenhar e medir o texto com [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] usando estático <xref:System.Windows.Forms.TextRenderer.DrawText%2A> e <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> métodos oferecidos pelo `TextRenderer` classe.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="1c9d6-106">Os métodos [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] também permitem especificar localização, fonte e formato.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="1c9d6-107">É possível escolher [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] ou [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para renderização de texto; entretanto, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] geralmente oferece melhor desempenho e medição de texto mais precisa.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="1c9d6-108">Outras classes que contribuem para a renderização de texto incluem `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, e `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c9d6-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1c9d6-109">In This Section</span></span>  
 [<span data-ttu-id="1c9d6-110">Como construir fontes e famílias de fontes</span><span class="sxs-lookup"><span data-stu-id="1c9d6-110">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="1c9d6-111">Mostra como criar objetos `Font` e `FontFamily`.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="1c9d6-112">Como desenhar texto em um local especificado</span><span class="sxs-lookup"><span data-stu-id="1c9d6-112">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="1c9d6-113">Descreve como desenhar texto em um local especificado [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c9d6-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="1c9d6-114">Como desenhar texto ajustado um retângulo</span><span class="sxs-lookup"><span data-stu-id="1c9d6-114">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="1c9d6-115">Explica como desenhar texto em um retângulo usando [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c9d6-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="1c9d6-116">Como desenhar texto com o GDI</span><span class="sxs-lookup"><span data-stu-id="1c9d6-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="1c9d6-117">Demonstra como usar [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] para desenhar texto.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="1c9d6-118">Como alinhar um texto desenhado</span><span class="sxs-lookup"><span data-stu-id="1c9d6-118">How to: Align Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 <span data-ttu-id="1c9d6-119">Mostra como formatar texto [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c9d6-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="1c9d6-120">Como criar texto vertical</span><span class="sxs-lookup"><span data-stu-id="1c9d6-120">How to: Create Vertical Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 <span data-ttu-id="1c9d6-121">Descreve como desenhar um texto alinhado verticalmente com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c9d6-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="1c9d6-122">Como definir paradas de tabulação em um texto desenhado</span><span class="sxs-lookup"><span data-stu-id="1c9d6-122">How to: Set Tab Stops in Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="1c9d6-123">Mostra como desenhar textos com paradas de tabulação com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c9d6-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="1c9d6-124">Como enumerar as fontes instaladas</span><span class="sxs-lookup"><span data-stu-id="1c9d6-124">How to: Enumerate Installed Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="1c9d6-125">Explica como listar os nomes das fontes instaladas.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="1c9d6-126">Como criar uma coleção de fontes privada</span><span class="sxs-lookup"><span data-stu-id="1c9d6-126">How to: Create a Private Font Collection</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="1c9d6-127">Descreve como criar um <xref:System.Drawing.Text.PrivateFontCollection> objeto.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="1c9d6-128">Como obter métricas de fontes</span><span class="sxs-lookup"><span data-stu-id="1c9d6-128">How to: Obtain Font Metrics</span></span>](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 <span data-ttu-id="1c9d6-129">Mostra como obter métricas de fonte, como subida e descida de células.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="1c9d6-130">Como usar suavização com texto</span><span class="sxs-lookup"><span data-stu-id="1c9d6-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="1c9d6-131">Explica como usar a suavização ao desenhar texto.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1c9d6-132">Referência</span><span class="sxs-lookup"><span data-stu-id="1c9d6-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="1c9d6-133">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="1c9d6-134">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="1c9d6-135">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="1c9d6-136">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="1c9d6-137">Descreve essa classe e contém links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1c9d6-137">Describes this class and contains links to all of its members.</span></span>
