---
title: 'Como: Enumerar fontes de sistema'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
ms.openlocfilehash: c7e81b5d1b70ba911a0b505219f7977e019038cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352432"
---
# <a name="how-to-enumerate-system-fonts"></a><span data-ttu-id="e373a-102">Como: Enumerar fontes de sistema</span><span class="sxs-lookup"><span data-stu-id="e373a-102">How to: Enumerate System Fonts</span></span>
## <a name="example"></a><span data-ttu-id="e373a-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e373a-103">Example</span></span>  
 <span data-ttu-id="e373a-104">O exemplo a seguir mostra como enumerar as fontes na coleção de fontes do sistema.</span><span class="sxs-lookup"><span data-stu-id="e373a-104">The following example shows how to enumerate the fonts in the system font collection.</span></span> <span data-ttu-id="e373a-105">O nome de família de fonte de cada <xref:System.Windows.Media.FontFamily> dentro de <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> é adicionado como um item de caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="e373a-105">The font family name of each <xref:System.Windows.Media.FontFamily> within <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> is added as an item to a combo box.</span></span>  
  
 [!code-csharp[TextOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 <span data-ttu-id="e373a-106">Se várias versões da mesma família de fonte residir no mesmo diretório, o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] enumeração de fonte retorna a versão mais recente da fonte.</span><span class="sxs-lookup"><span data-stu-id="e373a-106">If multiple versions of the same font family reside in the same directory, the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] font enumeration returns the most recent version of the font.</span></span> <span data-ttu-id="e373a-107">Se as informações de versão não fornece a resolução, a fonte com carimbo de hora mais recente será retornada.</span><span class="sxs-lookup"><span data-stu-id="e373a-107">If the version information does not provide resolution, the font with latest timestamp is returned.</span></span> <span data-ttu-id="e373a-108">Se as informações de carimbo de hora são equivalentes, o arquivo de fonte que é o primeiro em ordem alfabética será retornado.</span><span class="sxs-lookup"><span data-stu-id="e373a-108">If the timestamp information is equivalent, the font file that is first in alphabetical order is returned.</span></span>
