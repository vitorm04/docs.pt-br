---
title: "Como usar uma grade para layout automático"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d18563c44381a276d15996dff3f9552c46833b4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="a4307-102">Como usar uma grade para layout automático</span><span class="sxs-lookup"><span data-stu-id="a4307-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="a4307-103">Este exemplo descreve como usar uma grade na abordagem de layout automático para criar um aplicativo localizável.</span><span class="sxs-lookup"><span data-stu-id="a4307-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="a4307-104">Localização de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="a4307-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="a4307-105">Geralmente, localizadores precisam redimensionar e reposicionar elementos além de traduzir o texto.</span><span class="sxs-lookup"><span data-stu-id="a4307-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="a4307-106">No passado cada idioma que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] foi adaptado para ajuste necessário.</span><span class="sxs-lookup"><span data-stu-id="a4307-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="a4307-107">Agora com os recursos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] você pode criar elementos que reduzem a necessidade de ajuste.</span><span class="sxs-lookup"><span data-stu-id="a4307-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="a4307-108">A abordagem para escrever aplicativos que podem ser reposicionado e redimensionado mais facilmente é chamada `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="a4307-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="a4307-109">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo demonstra o uso de uma grade para posicionar alguns botões e texto.</span><span class="sxs-lookup"><span data-stu-id="a4307-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="a4307-110">Observe que a altura e largura das células são definidas como `Auto`; portanto, a célula que contém o botão com uma imagem ajusta para ajustar a imagem.</span><span class="sxs-lookup"><span data-stu-id="a4307-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="a4307-111">Porque o <xref:System.Windows.Controls.Grid> elemento pode ajustar a seu conteúdo pode ser útil quando seguirmos a abordagem de layout automático para projetar aplicativos que podem ser localizados.</span><span class="sxs-lookup"><span data-stu-id="a4307-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4307-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4307-112">Example</span></span>  
 <span data-ttu-id="a4307-113">O exemplo a seguir mostra como usar uma grade.</span><span class="sxs-lookup"><span data-stu-id="a4307-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="a4307-114">O gráfico a seguir mostra a saída do exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="a4307-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="a4307-115">![Exemplo de grade](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="a4307-115">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="a4307-116">Grade</span><span class="sxs-lookup"><span data-stu-id="a4307-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4307-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4307-117">See Also</span></span>  
 [<span data-ttu-id="a4307-118">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="a4307-118">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="a4307-119">Usar layout automático para criar um botão</span><span class="sxs-lookup"><span data-stu-id="a4307-119">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
