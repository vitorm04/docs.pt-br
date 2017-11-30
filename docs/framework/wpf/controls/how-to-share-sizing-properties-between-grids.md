---
title: Como compartilhar propriedades de dimensionamento entre grades
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0e3be0a0b550f6fbbc9876709094d4a23abe1a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="a831a-102">Como compartilhar propriedades de dimensionamento entre grades</span><span class="sxs-lookup"><span data-stu-id="a831a-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="a831a-103">Este exemplo mostra como compartilhar os dados de dimensionamento de colunas e linhas entre <xref:System.Windows.Controls.Grid> elementos para manter um dimensionamento consistente.</span><span class="sxs-lookup"><span data-stu-id="a831a-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a831a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a831a-104">Example</span></span>  
 <span data-ttu-id="a831a-105">O exemplo a seguir apresenta dois <xref:System.Windows.Controls.Grid> elementos como elementos filho de um pai <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="a831a-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="a831a-106">O <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> anexado a propriedade de <xref:System.Windows.Controls.Grid> é definido no pai <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="a831a-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="a831a-107">O exemplo manipula o valor da propriedade usando dois <xref:System.Windows.Controls.Button> elementos; cada elemento representa um dos valores de propriedade booliano.</span><span class="sxs-lookup"><span data-stu-id="a831a-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="a831a-108">Quando o <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> o valor da propriedade é definido como `true`, cada membro de coluna ou linha de uma <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> compartilha informações de dimensionamento, independentemente do conteúdo de uma linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="a831a-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="a831a-109">...</span><span class="sxs-lookup"><span data-stu-id="a831a-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="a831a-110">O seguinte exemplo de code-behind trata os métodos que o botão <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gera eventos.</span><span class="sxs-lookup"><span data-stu-id="a831a-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="a831a-111">O exemplo grava os resultados dessas chamadas de método para <xref:System.Windows.Controls.TextBlock> elementos relacionados ao uso obtém métodos para os novos valores de propriedade como cadeias de caracteres de saída.</span><span class="sxs-lookup"><span data-stu-id="a831a-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a831a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a831a-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [<span data-ttu-id="a831a-113">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="a831a-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
