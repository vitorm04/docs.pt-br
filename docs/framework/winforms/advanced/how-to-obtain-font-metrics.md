---
title: 'Como: Obter métricas de fontes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 5e37725363640bd02fc3e0f62f66d21151b497fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657253"
---
# <a name="how-to-obtain-font-metrics"></a><span data-ttu-id="1fae2-102">Como: Obter métricas de fontes</span><span class="sxs-lookup"><span data-stu-id="1fae2-102">How to: Obtain Font Metrics</span></span>
<span data-ttu-id="1fae2-103">O <xref:System.Drawing.FontFamily> classe fornece os seguintes métodos que recuperam várias métricas de uma combinação de estilo/família específica:</span><span class="sxs-lookup"><span data-stu-id="1fae2-103">The <xref:System.Drawing.FontFamily> class provides the following methods that retrieve various metrics for a particular family/style combination:</span></span>  
  
-   <span data-ttu-id="1fae2-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="1fae2-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="1fae2-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="1fae2-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="1fae2-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="1fae2-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="1fae2-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="1fae2-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span></span>  
  
 <span data-ttu-id="1fae2-108">Os números retornados por esses métodos são em unidades de design de fonte, portanto, eles são independentes do tamanho e das unidades de um determinado <xref:System.Drawing.Font> objeto.</span><span class="sxs-lookup"><span data-stu-id="1fae2-108">The numbers returned by these methods are in font design units, so they are independent of the size and units of a particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="1fae2-109">A ilustração a seguir mostra as diversas métricas.</span><span class="sxs-lookup"><span data-stu-id="1fae2-109">The following illustration shows the various metrics.</span></span>  
  
 <span data-ttu-id="1fae2-110">![Texto de fontes](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span><span class="sxs-lookup"><span data-stu-id="1fae2-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fae2-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1fae2-111">Example</span></span>  
 <span data-ttu-id="1fae2-112">O exemplo a seguir exibe as métricas para o estilo normal da família de fontes Arial.</span><span class="sxs-lookup"><span data-stu-id="1fae2-112">The following example displays the metrics for the regular style of the Arial font family.</span></span> <span data-ttu-id="1fae2-113">O código também cria uma <xref:System.Drawing.Font> objeto (com base na família Arial) com 16 pixels de tamanho e exibe as métricas (em pixels) para esse determinado <xref:System.Drawing.Font> objeto.</span><span class="sxs-lookup"><span data-stu-id="1fae2-113">The code also creates a <xref:System.Drawing.Font> object (based on the Arial family) with size 16 pixels and displays the metrics (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="1fae2-114">A ilustração a seguir mostra a saída do código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="1fae2-114">The following illustration shows the output of the example code.</span></span>  
  
 <span data-ttu-id="1fae2-115">![Texto de fontes](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span><span class="sxs-lookup"><span data-stu-id="1fae2-115">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span></span>  
  
 <span data-ttu-id="1fae2-116">Observe as duas primeiras linhas de saída na ilustração anterior.</span><span class="sxs-lookup"><span data-stu-id="1fae2-116">Note the first two lines of output in the preceding illustration.</span></span> <span data-ttu-id="1fae2-117">O <xref:System.Drawing.Font> objeto retorna um tamanho de 16 e o <xref:System.Drawing.FontFamily> object retorna uma altura de 2.048.</span><span class="sxs-lookup"><span data-stu-id="1fae2-117">The <xref:System.Drawing.Font> object returns a size of 16, and the <xref:System.Drawing.FontFamily> object returns an em height of 2,048.</span></span> <span data-ttu-id="1fae2-118">Esses dois números (16 e 2.048) são a chave para a conversão entre unidades de design de fonte e as unidades (em pixels nesse caso) do <xref:System.Drawing.Font> objeto.</span><span class="sxs-lookup"><span data-stu-id="1fae2-118">These two numbers (16 and 2,048) are the key to converting between font design units and the units (in this case pixels) of the <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="1fae2-119">Por exemplo, você pode converter o ascendente de unidades de design em pixels da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1fae2-119">For example, you can convert the ascent from design units to pixels as follows:</span></span>  
  
 <span data-ttu-id="1fae2-120">![Texto de fontes](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span><span class="sxs-lookup"><span data-stu-id="1fae2-120">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span></span>  
  
 <span data-ttu-id="1fae2-121">O código a seguir posiciona o texto verticalmente, definindo o <xref:System.Drawing.PointF.Y%2A> membro de dados de um <xref:System.Drawing.PointF> objeto.</span><span class="sxs-lookup"><span data-stu-id="1fae2-121">The following code positions text vertically by setting the <xref:System.Drawing.PointF.Y%2A> data member of a <xref:System.Drawing.PointF> object.</span></span> <span data-ttu-id="1fae2-122">A coordenada y é aumentada em `font.Height` para cada nova linha de texto.</span><span class="sxs-lookup"><span data-stu-id="1fae2-122">The y-coordinate is increased by `font.Height` for each new line of text.</span></span> <span data-ttu-id="1fae2-123">O <xref:System.Drawing.Font.Height%2A> propriedade de um <xref:System.Drawing.Font> object retorna o espaçamento entre linhas (em pixels) para esse determinado <xref:System.Drawing.Font> objeto.</span><span class="sxs-lookup"><span data-stu-id="1fae2-123">The <xref:System.Drawing.Font.Height%2A> property of a <xref:System.Drawing.Font> object returns the line spacing (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="1fae2-124">Neste exemplo, o número retornado por <xref:System.Drawing.Font.Height%2A> é 19.</span><span class="sxs-lookup"><span data-stu-id="1fae2-124">In this example, the number returned by <xref:System.Drawing.Font.Height%2A> is 19.</span></span> <span data-ttu-id="1fae2-125">Observe que esse é o mesmo número (arredondado para um número inteiro) obtido ao converter a métrica de espaçamento entre linhas em pixels.</span><span class="sxs-lookup"><span data-stu-id="1fae2-125">Note that this is the same as the number (rounded up to an integer) obtained by converting the line-spacing metric to pixels.</span></span>  
  
 <span data-ttu-id="1fae2-126">Observe que a altura em (também chamada de tamanho ou tamanho em) não é a soma do ascendente e do descendente.</span><span class="sxs-lookup"><span data-stu-id="1fae2-126">Note that the em height (also called size or em size) is not the sum of the ascent and the descent.</span></span> <span data-ttu-id="1fae2-127">A soma do ascendente e do descendente é chamada a altura da célula.</span><span class="sxs-lookup"><span data-stu-id="1fae2-127">The sum of the ascent and the descent is called the cell height.</span></span> <span data-ttu-id="1fae2-128">A altura da célula menos o entrelinhamento interno é igual à altura em.</span><span class="sxs-lookup"><span data-stu-id="1fae2-128">The cell height minus the internal leading is equal to the em height.</span></span> <span data-ttu-id="1fae2-129">A altura da célula mais o entrelinhamento externo é igual ao espaçamento entre linhas.</span><span class="sxs-lookup"><span data-stu-id="1fae2-129">The cell height plus the external leading is equal to the line spacing.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1fae2-130">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1fae2-130">Compiling the Code</span></span>  
 <span data-ttu-id="1fae2-131">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="1fae2-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fae2-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fae2-132">See also</span></span>
- [<span data-ttu-id="1fae2-133">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1fae2-133">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="1fae2-134">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="1fae2-134">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
