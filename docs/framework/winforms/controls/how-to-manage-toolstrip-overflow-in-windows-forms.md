---
title: Como gerenciar o estouro de ToolStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736152"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="03261-102">Como gerenciar o estouro de ToolStrip nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="03261-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>

<span data-ttu-id="03261-103">Quando todos os itens em um controle de <xref:System.Windows.Forms.ToolStrip> não couberem no espaço alocado, você poderá habilitar a funcionalidade de estouro na <xref:System.Windows.Forms.ToolStrip> e determinar o comportamento de estouro de <xref:System.Windows.Forms.ToolStripItem>s específicos.</span><span class="sxs-lookup"><span data-stu-id="03261-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>

<span data-ttu-id="03261-104">Quando você adiciona <xref:System.Windows.Forms.ToolStripItem>s que exigem mais espaço do que é alocado para o <xref:System.Windows.Forms.ToolStrip> dado o tamanho atual do formulário, um <xref:System.Windows.Forms.ToolStripOverflowButton> aparece automaticamente na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="03261-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="03261-105">O <xref:System.Windows.Forms.ToolStripOverflowButton> aparece e os itens habilitados para estouro são movidos para o menu suspenso de estouro.</span><span class="sxs-lookup"><span data-stu-id="03261-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="03261-106">Isso permite que você personalize e Priorize como seus <xref:System.Windows.Forms.ToolStrip> itens se ajustam adequadamente para diferentes tamanhos de formulário.</span><span class="sxs-lookup"><span data-stu-id="03261-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="03261-107">Você também pode alterar a aparência de seus itens quando eles se enquadram no estouro usando as propriedades <xref:System.Windows.Forms.ToolStripItem.Placement%2A> e <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> e o evento <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>.</span><span class="sxs-lookup"><span data-stu-id="03261-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="03261-108">Se você aumentar o formulário em tempo de design ou em tempo de execução, mais <xref:System.Windows.Forms.ToolStripItem>s poderão ser exibidos na <xref:System.Windows.Forms.ToolStrip> principal e a <xref:System.Windows.Forms.ToolStripOverflowButton> poderá até mesmo desaparecer até que você diminua o tamanho do formulário.</span><span class="sxs-lookup"><span data-stu-id="03261-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>

## <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="03261-109">Para habilitar o estouro em um controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="03261-109">To enable overflow on a ToolStrip control</span></span>

- <span data-ttu-id="03261-110">Verifique se a propriedade <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> não está definida como `false` para o <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="03261-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="03261-111">O padrão é `True`.</span><span class="sxs-lookup"><span data-stu-id="03261-111">The default is `True`.</span></span>

     <span data-ttu-id="03261-112">Quando <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> é `True` (o padrão), um <xref:System.Windows.Forms.ToolStripItem> é enviado para o menu suspenso de estouro quando o conteúdo da <xref:System.Windows.Forms.ToolStripItem> excede a largura de um <xref:System.Windows.Forms.ToolStrip> horizontal ou a altura de uma <xref:System.Windows.Forms.ToolStrip>vertical.</span><span class="sxs-lookup"><span data-stu-id="03261-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="03261-113">Especificar comportamento de estouro de um item ToolStripItem específico</span><span class="sxs-lookup"><span data-stu-id="03261-113">To specify overflow behavior of a specific ToolStripItem</span></span>

- <span data-ttu-id="03261-114">Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> do <xref:System.Windows.Forms.ToolStripItem> para o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="03261-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="03261-115">As possibilidades são `Always`, `Never` e `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="03261-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="03261-116">O padrão é `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="03261-116">The default is `AsNeeded`.</span></span>

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a><span data-ttu-id="03261-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="03261-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="03261-118">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="03261-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="03261-119">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="03261-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="03261-120">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="03261-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
