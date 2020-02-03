---
title: Controle TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms]
- controls [Windows Forms], sizing
- sizing [Windows Forms], automatic
- layout [Windows Forms], TableLayoutPanel control
- automatic sizing
ms.assetid: f55175c6-424e-4782-a86e-3f79c1550235
ms.openlocfilehash: 12b40d4ce47770b3ffe9bfdebca74eca4afd3dd1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735512"
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="311a8-102">Controle TableLayoutPanel (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="311a8-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="311a8-103">O controle de <xref:System.Windows.Forms.TableLayoutPanel> organiza seu conteúdo em uma grade.</span><span class="sxs-lookup"><span data-stu-id="311a8-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="311a8-104">Como o layout é executado tanto em tempo de design quanto em tempo de execução, ele pode ser alterado dinamicamente à medida que o ambiente do aplicativo muda.</span><span class="sxs-lookup"><span data-stu-id="311a8-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="311a8-105">Assim, os controles no painel têm a capacidade de redimensionar proporcionalmente, portanto ele pode responder a alterações como o redimensionamento do controle pai ou à alteração de comprimento do texto devido à localização.</span><span class="sxs-lookup"><span data-stu-id="311a8-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="311a8-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="311a8-106">In This Section</span></span>  
 [<span data-ttu-id="311a8-107">Visão geral do controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="311a8-107">TableLayoutPanel Control Overview</span></span>](tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="311a8-108">Apresenta os conceitos gerais do controle de <xref:System.Windows.Forms.TableLayoutPanel>, que permite criar um layout com linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="311a8-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="311a8-109">Práticas recomendadas para o controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="311a8-109">Best Practices for the TableLayoutPanel Control</span></span>](best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="311a8-110">Descreve as recomendações para ajudá-lo a obter o máximo dos recursos de layout do controle de <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="311a8-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="311a8-111">Comportamento de AutoSize no controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="311a8-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="311a8-112">Explica as maneiras em que o controle de <xref:System.Windows.Forms.TableLayoutPanel> dá suporte ao comportamento de dimensionamento automático.</span><span class="sxs-lookup"><span data-stu-id="311a8-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="311a8-113">Como ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="311a8-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="311a8-114">Mostra como ancorar e encaixar controles filho em um controle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="311a8-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="311a8-115">Como criar um layout dos Windows Forms que responda bem à localização</span><span class="sxs-lookup"><span data-stu-id="311a8-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="311a8-116">Demonstra o uso de um controle <xref:System.Windows.Forms.TableLayoutPanel> para criar um formulário que responda bem à localização.</span><span class="sxs-lookup"><span data-stu-id="311a8-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="311a8-117">Como criar um Windows Form redimensionável para entrada de dados</span><span class="sxs-lookup"><span data-stu-id="311a8-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="311a8-118">Demonstra o uso de um controle <xref:System.Windows.Forms.TableLayoutPanel> para criar um formulário que responda bem ao redimensionamento.</span><span class="sxs-lookup"><span data-stu-id="311a8-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1. [<span data-ttu-id="311a8-119">Como alinhar e alongar um controle em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="311a8-119">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="311a8-120">Como abranger linhas e colunas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="311a8-120">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3. [<span data-ttu-id="311a8-121">Como editar colunas e linhas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="311a8-121">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="311a8-122">Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="311a8-122">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="reference"></a><span data-ttu-id="311a8-123">Referência</span><span class="sxs-lookup"><span data-stu-id="311a8-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="311a8-124">Fornece documentação de referência para o controle de <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="311a8-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="311a8-125">Fornece documentação de referência para o tipo de <xref:System.Windows.Forms.TableLayoutSettings>.</span><span class="sxs-lookup"><span data-stu-id="311a8-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="311a8-126">Fornece documentação de referência para o controle de <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="311a8-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="311a8-127">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="311a8-127">Related Sections</span></span>  
 [<span data-ttu-id="311a8-128">Localização</span><span class="sxs-lookup"><span data-stu-id="311a8-128">Localization</span></span>](../../../standard/globalization-localization/localization.md)  
 <span data-ttu-id="311a8-129">Fornece uma visão geral dos tópicos relacionados à localização.</span><span class="sxs-lookup"><span data-stu-id="311a8-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="311a8-130">Consulte também [Localizando aplicativos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="311a8-130">Also see [Localizing Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span></span>
