---
title: Comportamento de AutoSize no controle TableLayoutPanel
ms.date: 03/30/2017
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
ms.openlocfilehash: 466edeee5f45ec72ef265ef4855049c7852641b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164964"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="738e0-102">Comportamento de AutoSize no controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="738e0-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="738e0-103">Comportamentos distintos de AutoSize</span><span class="sxs-lookup"><span data-stu-id="738e0-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="738e0-104">O <xref:System.Windows.Forms.TableLayoutPanel> controle dá suporte ao comportamento de dimensionamento automático das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="738e0-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="738e0-105">Por meio de <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade;</span><span class="sxs-lookup"><span data-stu-id="738e0-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="738e0-106">Por meio de <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriedade no <xref:System.Windows.Forms.TableLayoutPanel> estilos de coluna e linha do controle.</span><span class="sxs-lookup"><span data-stu-id="738e0-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="738e0-107">A propriedade AutoSize com estilos de coluna e linha</span><span class="sxs-lookup"><span data-stu-id="738e0-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="738e0-108">A tabela a seguir descreve a interação entre o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade e o <xref:System.Windows.Forms.TableLayoutPanel> estilos de coluna e linha do controle.</span><span class="sxs-lookup"><span data-stu-id="738e0-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="738e0-109">Configuração de AutoSize</span><span class="sxs-lookup"><span data-stu-id="738e0-109">AutoSize setting</span></span>|<span data-ttu-id="738e0-110">Interação de estilo</span><span class="sxs-lookup"><span data-stu-id="738e0-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="738e0-111">O <xref:System.Windows.Forms.TableLayoutPanel> controle prossegue da esquerda para a direita e aloca espaço para a coluna ou linha ou na seguinte ordem.</span><span class="sxs-lookup"><span data-stu-id="738e0-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="738e0-112">1.  Se o <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> estiver definida como <xref:System.Windows.Forms.SizeType.Absolute>, o número de pixels especificado por <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> é alocado.</span><span class="sxs-lookup"><span data-stu-id="738e0-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="738e0-113">2.  Se o <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> estiver definida como <xref:System.Windows.Forms.SizeType.AutoSize>, o número de pixels retornados pelo controle do filho <xref:System.Windows.Forms.Control.GetPreferredSize%2A> método é alocado.</span><span class="sxs-lookup"><span data-stu-id="738e0-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="738e0-114">3.  Após o espaço para todos os <xref:System.Windows.Forms.SizeType.Absolute> e <xref:System.Windows.Forms.SizeType.AutoSize> linhas ou colunas é alocado, todas as colunas ou linhas com <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> definido como <xref:System.Windows.Forms.SizeType.Percent> são usadas para alocar proporcionalmente o espaço livre restante</span><span class="sxs-lookup"><span data-stu-id="738e0-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="738e0-115">Semelhante à interação anterior, com a exceção que <xref:System.Windows.Forms.SizeType.Percent> colunas ou linhas adquirem um aspecto de dimensionamento automático.</span><span class="sxs-lookup"><span data-stu-id="738e0-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="738e0-116">O <xref:System.Windows.Forms.TableLayoutPanel> controle se expande a coluna ou linha para criar o espaço livre adequado, para que nenhuma coluna ou linha com <xref:System.Windows.Forms.SizeType.Percent> estilo corte seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="738e0-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="738e0-117">O <xref:System.Windows.Forms.TableLayoutPanel> controle aloca novo espaço proporcionalmente acordo com ao <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="738e0-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="738e0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="738e0-118">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="738e0-119">Visão geral do controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="738e0-119">TableLayoutPanel Control Overview</span></span>](tablelayoutpanel-control-overview.md)
