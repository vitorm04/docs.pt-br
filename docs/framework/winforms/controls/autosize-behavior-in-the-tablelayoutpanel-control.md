---
title: Comportamento de AutoSize no controle TableLayoutPanel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d4813b7bd37c0c5bd9b04b37cb825067b35ce3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="c689e-102">Comportamento de AutoSize no controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c689e-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="c689e-103">Comportamentos distintos de AutoSize</span><span class="sxs-lookup"><span data-stu-id="c689e-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="c689e-104">O <xref:System.Windows.Forms.TableLayoutPanel> controle oferece suporte ao comportamento de dimensionamento automático das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c689e-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="c689e-105">Por meio de <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade;</span><span class="sxs-lookup"><span data-stu-id="c689e-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="c689e-106">Por meio de <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriedade o <xref:System.Windows.Forms.TableLayoutPanel> estilos de coluna e linha do controle.</span><span class="sxs-lookup"><span data-stu-id="c689e-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="c689e-107">A propriedade AutoSize com estilos de coluna e linha</span><span class="sxs-lookup"><span data-stu-id="c689e-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="c689e-108">A tabela a seguir descreve a interação entre o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade e o <xref:System.Windows.Forms.TableLayoutPanel> estilos de linha e coluna do controle.</span><span class="sxs-lookup"><span data-stu-id="c689e-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="c689e-109">Configuração de AutoSize</span><span class="sxs-lookup"><span data-stu-id="c689e-109">AutoSize setting</span></span>|<span data-ttu-id="c689e-110">Interação de estilo</span><span class="sxs-lookup"><span data-stu-id="c689e-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="c689e-111">O <xref:System.Windows.Forms.TableLayoutPanel> controle continua a partir da esquerda para a direita e aloca espaço para a coluna ou linha ou na seguinte ordem.</span><span class="sxs-lookup"><span data-stu-id="c689e-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="c689e-112">1.  Se o <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> está definida como <xref:System.Windows.Forms.SizeType.Absolute>, o número de pixels especificado por <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> é alocada.</span><span class="sxs-lookup"><span data-stu-id="c689e-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="c689e-113">2.  Se o <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> está definida como <xref:System.Windows.Forms.SizeType.AutoSize>, o número de pixels retornado do controle filho <xref:System.Windows.Forms.Control.GetPreferredSize%2A> método é alocado.</span><span class="sxs-lookup"><span data-stu-id="c689e-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="c689e-114">3.  Depois de espaço para todos os <xref:System.Windows.Forms.SizeType.Absolute> e <xref:System.Windows.Forms.SizeType.AutoSize> colunas ou linhas é alocada, algumas colunas ou linhas com <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> definida como <xref:System.Windows.Forms.SizeType.Percent> são usadas para alocar proporcionalmente o espaço livre restante</span><span class="sxs-lookup"><span data-stu-id="c689e-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="c689e-115">Semelhante à interação anterior, com a exceção que <xref:System.Windows.Forms.SizeType.Percent> colunas ou linhas adquirem um aspecto de dimensionamento automático.</span><span class="sxs-lookup"><span data-stu-id="c689e-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="c689e-116">O <xref:System.Windows.Forms.TableLayoutPanel> expande o controle de coluna ou linha para criar espaço livre suficiente, para que nenhuma coluna ou linha com <xref:System.Windows.Forms.SizeType.Percent> estilo recorta seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c689e-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="c689e-117">O <xref:System.Windows.Forms.TableLayoutPanel> controle aloca novo espaço proporcionalmente acordo com o <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c689e-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c689e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c689e-118">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="c689e-119">Visão geral do controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c689e-119">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
