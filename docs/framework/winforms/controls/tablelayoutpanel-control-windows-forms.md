---
title: Controle TableLayoutPanel (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms]
- controls [Windows Forms], sizing
- sizing [Windows Forms], automatic
- layout [Windows Forms], TableLayoutPanel control
- automatic sizing
ms.assetid: f55175c6-424e-4782-a86e-3f79c1550235
ms.openlocfilehash: b51d3bd8e9d8816dfae6c10fc752adb0b3cea59c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932490"
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="db5ab-102">Controle TableLayoutPanel (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="db5ab-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="db5ab-103">O <xref:System.Windows.Forms.TableLayoutPanel> controle organiza seu conteúdo em uma grade.</span><span class="sxs-lookup"><span data-stu-id="db5ab-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="db5ab-104">Como o layout é executado tanto em tempo de design quanto em tempo de execução, ele pode ser alterado dinamicamente à medida que o ambiente do aplicativo muda.</span><span class="sxs-lookup"><span data-stu-id="db5ab-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="db5ab-105">Assim, os controles no painel têm a capacidade de redimensionar proporcionalmente, portanto ele pode responder a alterações como o redimensionamento do controle pai ou à alteração de comprimento do texto devido à localização.</span><span class="sxs-lookup"><span data-stu-id="db5ab-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db5ab-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="db5ab-106">In This Section</span></span>  
 [<span data-ttu-id="db5ab-107">Visão geral do controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="db5ab-107">TableLayoutPanel Control Overview</span></span>](tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="db5ab-108">Apresenta os conceitos gerais do <xref:System.Windows.Forms.TableLayoutPanel> controle, que permite que você crie um layout com linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="db5ab-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="db5ab-109">Práticas recomendadas para o controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="db5ab-109">Best Practices for the TableLayoutPanel Control</span></span>](best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="db5ab-110">Descreve as recomendações para ajudá-lo a aproveitar ao máximo os recursos de layout do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="db5ab-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="db5ab-111">Comportamento de AutoSize no controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="db5ab-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="db5ab-112">Explica as formas nas quais o <xref:System.Windows.Forms.TableLayoutPanel> controle dá suporte ao comportamento de dimensionamento automático.</span><span class="sxs-lookup"><span data-stu-id="db5ab-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="db5ab-113">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="db5ab-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="db5ab-114">Mostra como ancorar e encaixar controles filho em um <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="db5ab-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="db5ab-115">Como: Projetar um Layout de formulários do Windows que responde bem à localização</span><span class="sxs-lookup"><span data-stu-id="db5ab-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="db5ab-116">Demonstra como usar um <xref:System.Windows.Forms.TableLayoutPanel> controle para criar um formulário que responde bem à localização.</span><span class="sxs-lookup"><span data-stu-id="db5ab-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="db5ab-117">Como: Criar um formulário do Windows redimensionável para entrada de dados</span><span class="sxs-lookup"><span data-stu-id="db5ab-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="db5ab-118">Demonstra como usar um <xref:System.Windows.Forms.TableLayoutPanel> controle para criar um formulário que responde bem ao redimensionamento.</span><span class="sxs-lookup"><span data-stu-id="db5ab-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1. [<span data-ttu-id="db5ab-119">Como: Alinhar e Alongar um controle em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="db5ab-119">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="db5ab-120">Como: Abranger linhas e colunas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="db5ab-120">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3. [<span data-ttu-id="db5ab-121">Como: Editar colunas e linhas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="db5ab-121">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="db5ab-122">Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="db5ab-122">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="reference"></a><span data-ttu-id="db5ab-123">Referência</span><span class="sxs-lookup"><span data-stu-id="db5ab-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="db5ab-124">Fornece documentação de referência para o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="db5ab-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="db5ab-125">Fornece documentação de referência para o <xref:System.Windows.Forms.TableLayoutSettings> tipo.</span><span class="sxs-lookup"><span data-stu-id="db5ab-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="db5ab-126">Fornece documentação de referência para o <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="db5ab-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="db5ab-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="db5ab-127">Related Sections</span></span>  
 [<span data-ttu-id="db5ab-128">Localização</span><span class="sxs-lookup"><span data-stu-id="db5ab-128">Localization</span></span>](../../../standard/globalization-localization/localization.md)  
 <span data-ttu-id="db5ab-129">Fornece uma visão geral dos tópicos relacionados à localização.</span><span class="sxs-lookup"><span data-stu-id="db5ab-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="db5ab-130">Consulte também [localizando aplicativos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="db5ab-130">Also see [Localizing Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span></span>
