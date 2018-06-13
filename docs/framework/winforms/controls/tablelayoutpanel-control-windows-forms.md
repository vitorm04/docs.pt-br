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
ms.openlocfilehash: 3615ab1f9a9076b8db0e5fde1e5bd4a1a804f3bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538522"
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="44e13-102">Controle TableLayoutPanel (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="44e13-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="44e13-103">O <xref:System.Windows.Forms.TableLayoutPanel> controle organiza seu conteúdo em uma grade.</span><span class="sxs-lookup"><span data-stu-id="44e13-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="44e13-104">Como o layout é executado tanto em tempo de design quanto em tempo de execução, ele pode ser alterado dinamicamente à medida que o ambiente do aplicativo muda.</span><span class="sxs-lookup"><span data-stu-id="44e13-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="44e13-105">Assim, os controles no painel têm a capacidade de redimensionar proporcionalmente, portanto ele pode responder a alterações como o redimensionamento do controle pai ou à alteração de comprimento do texto devido à localização.</span><span class="sxs-lookup"><span data-stu-id="44e13-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44e13-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="44e13-106">In This Section</span></span>  
 [<span data-ttu-id="44e13-107">Visão geral do controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="44e13-107">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="44e13-108">Apresenta os conceitos gerais do <xref:System.Windows.Forms.TableLayoutPanel> controle, que permite que você crie um layout com linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="44e13-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="44e13-109">Práticas recomendadas para o controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="44e13-109">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="44e13-110">Descreve as recomendações que ajudarão você a aproveitar ao máximo os recursos de layout do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="44e13-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="44e13-111">Comportamento de AutoSize no controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="44e13-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="44e13-112">Explica as maneiras em que o <xref:System.Windows.Forms.TableLayoutPanel> controle oferece suporte ao comportamento de dimensionamento automático.</span><span class="sxs-lookup"><span data-stu-id="44e13-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="44e13-113">Como ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="44e13-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="44e13-114">Mostra como ancorar e encaixar controles filho em um <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="44e13-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="44e13-115">Como criar um layout dos Windows Forms que responda bem à localização</span><span class="sxs-lookup"><span data-stu-id="44e13-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="44e13-116">Demonstra como usar um <xref:System.Windows.Forms.TableLayoutPanel> controle para criar um formulário que responde bem à localização.</span><span class="sxs-lookup"><span data-stu-id="44e13-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="44e13-117">Como criar um Windows Form redimensionável para entrada de dados</span><span class="sxs-lookup"><span data-stu-id="44e13-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="44e13-118">Demonstra como usar um <xref:System.Windows.Forms.TableLayoutPanel> controle para criar um formulário que responde bem à redimensionamento.</span><span class="sxs-lookup"><span data-stu-id="44e13-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1.  <span data-ttu-id="44e13-119">[Como alinhar e alongar um controle em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="44e13-119">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="44e13-120">[Como abranger linhas e colunas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="44e13-120">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="44e13-121">[Como editar colunas e linhas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="44e13-121">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="44e13-122">[Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="44e13-122">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="44e13-123">Referência</span><span class="sxs-lookup"><span data-stu-id="44e13-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="44e13-124">Fornece documentação de referência para o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="44e13-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="44e13-125">Fornece documentação de referência para o <xref:System.Windows.Forms.TableLayoutSettings> tipo.</span><span class="sxs-lookup"><span data-stu-id="44e13-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="44e13-126">Fornece documentação de referência para o <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="44e13-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="44e13-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="44e13-127">Related Sections</span></span>  
 [<span data-ttu-id="44e13-128">Localização</span><span class="sxs-lookup"><span data-stu-id="44e13-128">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="44e13-129">Fornece uma visão geral dos tópicos relacionados à localização.</span><span class="sxs-lookup"><span data-stu-id="44e13-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="44e13-130">Veja também [Localizando aplicativos](http://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) ou [Localizando aplicativos](http://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="44e13-130">Also see [Localizing Applications](http://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) or [Localizing Applications](http://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span></span>
