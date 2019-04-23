---
title: 'Como: Alterar a aparência de texto e imagens de ToolStrip nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: 5c326c8f6a56c934d317305f85f4c88e95e75f8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088464"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="0438f-102">Como: Alterar a aparência de texto e imagens de ToolStrip nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0438f-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="0438f-103">Você pode controlar se o texto e imagens são exibidas em uma <xref:System.Windows.Forms.ToolStripItem> e como eles são alinhados relativos uns aos outros e a <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="0438f-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="0438f-104">Para definir o que é exibido em um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="0438f-104">To define what is displayed on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="0438f-105">Defina o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade para o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="0438f-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="0438f-106">As possibilidades são `Image`, `ImageAndText`, `None`, e `Text`.</span><span class="sxs-lookup"><span data-stu-id="0438f-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="0438f-107">O padrão é `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="0438f-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="0438f-108">Para alinhar o texto em um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="0438f-108">To align text on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="0438f-109">Defina o <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> propriedade para o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="0438f-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="0438f-110">As possibilidades são qualquer combinação de parte superior, intermediária e inferior com esquerda, centro e direita.</span><span class="sxs-lookup"><span data-stu-id="0438f-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="0438f-111">O padrão é `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="0438f-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="0438f-112">Para alinhar uma imagem em um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="0438f-112">To align an image on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="0438f-113">Defina o <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> propriedade para o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="0438f-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="0438f-114">As possibilidades são qualquer combinação de parte superior, intermediária e inferior com esquerda, centro e direita.</span><span class="sxs-lookup"><span data-stu-id="0438f-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="0438f-115">O padrão é `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="0438f-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="0438f-116">Para definir como imagens e texto ToolStripItem são exibidas em relação uns aos outros</span><span class="sxs-lookup"><span data-stu-id="0438f-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
-   <span data-ttu-id="0438f-117">Defina o <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriedade para o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="0438f-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="0438f-118">As possibilidades são `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage` e `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="0438f-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="0438f-119">O padrão é `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="0438f-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0438f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0438f-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="0438f-121">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0438f-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="0438f-122">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0438f-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="0438f-123">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0438f-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
