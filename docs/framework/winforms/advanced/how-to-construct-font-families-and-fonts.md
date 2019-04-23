---
title: 'Como: construir fontes e famílias de fontes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: 0a9dcd00d4bc3e64ae4fc9a1d4884fac18521825
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181214"
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="dfa14-102">Como: construir fontes e famílias de fontes</span><span class="sxs-lookup"><span data-stu-id="dfa14-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="dfa14-103">agrupa fontes com a mesma face de tipo, mas diferentes estilos em famílias de fontes.</span><span class="sxs-lookup"><span data-stu-id="dfa14-103">groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="dfa14-104">Por exemplo, a família de fonte Arial contém as seguintes fontes:</span><span class="sxs-lookup"><span data-stu-id="dfa14-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="dfa14-105">Arial Regular</span><span class="sxs-lookup"><span data-stu-id="dfa14-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="dfa14-106">Arial Bold</span><span class="sxs-lookup"><span data-stu-id="dfa14-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="dfa14-107">Arial Italic</span><span class="sxs-lookup"><span data-stu-id="dfa14-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="dfa14-108">Arial Bold Italic</span><span class="sxs-lookup"><span data-stu-id="dfa14-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="dfa14-109">usa quatro estilos de famílias de formato: regular, negrito, itálico e negrito e itálico.</span><span class="sxs-lookup"><span data-stu-id="dfa14-109">uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="dfa14-110">Adjetivos como *estreito* e *arredondado* não são considerados estilos; em vez disso, eles são parte do nome da família.</span><span class="sxs-lookup"><span data-stu-id="dfa14-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="dfa14-111">Por exemplo, Arial Narrow é uma família de fontes com os seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="dfa14-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="dfa14-112">Arial Narrow Regular</span><span class="sxs-lookup"><span data-stu-id="dfa14-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="dfa14-113">Arial Narrow Bold</span><span class="sxs-lookup"><span data-stu-id="dfa14-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="dfa14-114">Arial Narrow Italic</span><span class="sxs-lookup"><span data-stu-id="dfa14-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="dfa14-115">Arial Narrow Bold Italic</span><span class="sxs-lookup"><span data-stu-id="dfa14-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="dfa14-116">Antes de você pode desenhar texto com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você precisa construir uma <xref:System.Drawing.FontFamily> objeto e um <xref:System.Drawing.Font> objeto.</span><span class="sxs-lookup"><span data-stu-id="dfa14-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="dfa14-117">O <xref:System.Drawing.FontFamily> objeto Especifica a face de tipos (por exemplo, Arial) e o <xref:System.Drawing.Font> objeto Especifica o tamanho, estilo e unidades.</span><span class="sxs-lookup"><span data-stu-id="dfa14-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfa14-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfa14-118">Example</span></span>  
 <span data-ttu-id="dfa14-119">O exemplo a seguir constrói uma fonte Arial de estilo regular com um tamanho de 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="dfa14-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="dfa14-120">No código a seguir, o primeiro argumento passado para o <xref:System.Drawing.Font.%23ctor%2A> construtor é o <xref:System.Drawing.FontFamily> objeto.</span><span class="sxs-lookup"><span data-stu-id="dfa14-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="dfa14-121">O segundo argumento especifica o tamanho da fonte medido em unidades identificadas pelo quarto argumento.</span><span class="sxs-lookup"><span data-stu-id="dfa14-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="dfa14-122">O terceiro argumento identifica o estilo.</span><span class="sxs-lookup"><span data-stu-id="dfa14-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="dfa14-123"><xref:System.Drawing.GraphicsUnit.Pixel> é um membro do <xref:System.Drawing.GraphicsUnit> enumeração, e <xref:System.Drawing.FontStyle.Regular> é um membro do <xref:System.Drawing.FontStyle> enumeração.</span><span class="sxs-lookup"><span data-stu-id="dfa14-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dfa14-124">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="dfa14-124">Compiling the Code</span></span>  
 <span data-ttu-id="dfa14-125">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="dfa14-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa14-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfa14-126">See also</span></span>

- [<span data-ttu-id="dfa14-127">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="dfa14-127">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="dfa14-128">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dfa14-128">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
