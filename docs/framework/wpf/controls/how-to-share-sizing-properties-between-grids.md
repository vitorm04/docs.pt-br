---
title: 'Como: Compartilhar propriedades de dimensionamento entre grades'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: bd0f812ce9a15628bd0bddf3a88e898311f0a9d3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373121"
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="8da99-102">Como: Compartilhar propriedades de dimensionamento entre grades</span><span class="sxs-lookup"><span data-stu-id="8da99-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="8da99-103">Este exemplo mostra como compartilhar os dados de dimensionamento de colunas e linhas entre <xref:System.Windows.Controls.Grid> elementos para manter um dimensionamento consistente.</span><span class="sxs-lookup"><span data-stu-id="8da99-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8da99-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8da99-104">Example</span></span>  
 <span data-ttu-id="8da99-105">O exemplo a seguir apresenta duas <xref:System.Windows.Controls.Grid> elementos como elementos filho de um pai <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="8da99-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="8da99-106">O <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> anexados a propriedade de <xref:System.Windows.Controls.Grid> é definido no pai <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="8da99-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="8da99-107">O exemplo manipula o valor da propriedade usando dois <xref:System.Windows.Controls.Button> elementos; cada elemento representa um dos valores de propriedade booliana.</span><span class="sxs-lookup"><span data-stu-id="8da99-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="8da99-108">Quando o <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> o valor da propriedade é definido como `true`, cada membro de coluna ou linha de uma <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> compartilha informações de dimensionamento, independentemente do conteúdo de uma linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="8da99-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="8da99-109">...</span><span class="sxs-lookup"><span data-stu-id="8da99-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="8da99-110">O exemplo de code-behind a seguir trata os métodos que o botão <xref:System.Windows.Controls.Primitives.ButtonBase.Click> aciona eventos.</span><span class="sxs-lookup"><span data-stu-id="8da99-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="8da99-111">O exemplo grava os resultados dessas chamadas de método <xref:System.Windows.Controls.TextBlock> métodos para os novos valores de propriedade como cadeias de caracteres de saída de get de elementos relacionados ao uso.</span><span class="sxs-lookup"><span data-stu-id="8da99-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8da99-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8da99-112">See also</span></span>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>
- [<span data-ttu-id="8da99-113">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="8da99-113">Panels Overview</span></span>](panels-overview.md)
