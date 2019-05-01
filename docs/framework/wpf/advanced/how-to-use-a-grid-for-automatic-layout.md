---
title: 'Como: Usar uma grade para layout automático'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 590ad7292fea572b20ccaa09ce2886724e004a6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052398"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="c3142-102">Como: Usar uma grade para layout automático</span><span class="sxs-lookup"><span data-stu-id="c3142-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="c3142-103">Este exemplo descreve como usar uma grade na abordagem de layout automático para criar um aplicativo localizável.</span><span class="sxs-lookup"><span data-stu-id="c3142-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="c3142-104">Localização de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="c3142-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="c3142-105">Geralmente, localizadores precisam redimensionar e reposicionar elementos além de traduzir o texto.</span><span class="sxs-lookup"><span data-stu-id="c3142-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="c3142-106">No passado cada idioma que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] foi adaptado exigia um ajuste.</span><span class="sxs-lookup"><span data-stu-id="c3142-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="c3142-107">Agora, com os recursos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] você pode criar elementos que reduzem a necessidade de ajuste.</span><span class="sxs-lookup"><span data-stu-id="c3142-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="c3142-108">A abordagem para escrever aplicativos que podem ser mais facilmente redimensionados e reposicionados é chamada `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="c3142-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="c3142-109">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo demonstra como usar uma grade para posicionar alguns botões e texto.</span><span class="sxs-lookup"><span data-stu-id="c3142-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="c3142-110">Observe que a altura e largura das células são definidas como `Auto`; portanto, a célula que contém o botão com uma imagem é ajustada para se adaptar à imagem.</span><span class="sxs-lookup"><span data-stu-id="c3142-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="c3142-111">Porque o <xref:System.Windows.Controls.Grid> elemento pode ajustar a seu conteúdo pode ser útil quando adotando a abordagem de layout automático para projetar aplicativos que podem ser localizados.</span><span class="sxs-lookup"><span data-stu-id="c3142-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3142-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3142-112">Example</span></span>  
 <span data-ttu-id="c3142-113">O exemplo a seguir mostra como usar uma grade.</span><span class="sxs-lookup"><span data-stu-id="c3142-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="c3142-114">O gráfico a seguir mostra a saída do exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="c3142-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="c3142-115">![Exemplo de grade](./media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="c3142-115">![Grid example](./media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="c3142-116">Grade</span><span class="sxs-lookup"><span data-stu-id="c3142-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3142-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3142-117">See also</span></span>

- [<span data-ttu-id="c3142-118">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="c3142-118">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
- [<span data-ttu-id="c3142-119">Usar layout automático para criar um botão</span><span class="sxs-lookup"><span data-stu-id="c3142-119">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
