---
title: 'Como: Abranger linhas e colunas em um controle TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039693"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="1ae6a-102">Como: Abranger linhas e colunas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1ae6a-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="1ae6a-103">Controles em um <xref:System.Windows.Forms.TableLayoutPanel> controle podem abranger linhas e colunas adjacentes.</span><span class="sxs-lookup"><span data-stu-id="1ae6a-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>

## <a name="to-span-columns-and-rows"></a><span data-ttu-id="1ae6a-104">Para abranger colunas e linhas</span><span class="sxs-lookup"><span data-stu-id="1ae6a-104">To span columns and rows</span></span>

1. <span data-ttu-id="1ae6a-105">Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="1ae6a-105">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="1ae6a-106">Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para a célula superior <xref:System.Windows.Forms.TableLayoutPanel> esquerda do controle.</span><span class="sxs-lookup"><span data-stu-id="1ae6a-106">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="1ae6a-107">Defina a <xref:System.Windows.Forms.Button> propriedade **ColumnSpan** do controle como **2**.</span><span class="sxs-lookup"><span data-stu-id="1ae6a-107">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="1ae6a-108">Observe que o <xref:System.Windows.Forms.Button> controle abrange a primeira e a segunda colunas.</span><span class="sxs-lookup"><span data-stu-id="1ae6a-108">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>

4. <span data-ttu-id="1ae6a-109">Defina a <xref:System.Windows.Forms.Button> propriedade **RowSpan** do controle como **2**.</span><span class="sxs-lookup"><span data-stu-id="1ae6a-109">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="1ae6a-110">Observe que o <xref:System.Windows.Forms.Button> controle abrange a primeira e a segunda linhas.</span><span class="sxs-lookup"><span data-stu-id="1ae6a-110">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>

5. <span data-ttu-id="1ae6a-111">Defina a <xref:System.Windows.Forms.Button> propriedade **ColumnSpan** do controle como **1**.</span><span class="sxs-lookup"><span data-stu-id="1ae6a-111">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="1ae6a-112">Observe que o <xref:System.Windows.Forms.Button> controle é movido para a primeira coluna e abrange a primeira e a segunda linhas.</span><span class="sxs-lookup"><span data-stu-id="1ae6a-112">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ae6a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ae6a-113">See also</span></span>

- [<span data-ttu-id="1ae6a-114">Controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1ae6a-114">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
