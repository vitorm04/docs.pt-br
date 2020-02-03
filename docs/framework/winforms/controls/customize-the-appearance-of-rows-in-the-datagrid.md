---
title: Personalizar a aparência de linhas no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 099b2104e7a4887aa846c4d65273db2dd4f60559
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744034"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6fcdd-102">Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6fcdd-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6fcdd-103">Você pode controlar a aparência de <xref:System.Windows.Forms.DataGridView> linhas manipulando um ou ambos os eventos <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6fcdd-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="6fcdd-104">Esses eventos são projetados para que você possa pintar apenas o que você deseja ao permitir que o controle de <xref:System.Windows.Forms.DataGridView> pinte o resto.</span><span class="sxs-lookup"><span data-stu-id="6fcdd-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="6fcdd-105">Por exemplo, se você quiser pintar um plano de fundo personalizado, poderá manipular o evento <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> e permitir que as células individuais Pinte seu próprio conteúdo em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="6fcdd-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="6fcdd-106">Como alternativa, você pode permitir que as células sejam pintadas e adicionar conteúdo de primeiro plano personalizado em um manipulador para o evento <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6fcdd-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="6fcdd-107">Você também pode desabilitar a pintura de célula e pintar tudo por conta própria em um manipulador de eventos <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6fcdd-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="6fcdd-108">O exemplo de código a seguir implementa manipuladores para ambos os eventos a fim de fornecer uma tela de fundo de seleção do gradiente e algum conteúdo de primeiro plano personalizado que abrange várias colunas.</span><span class="sxs-lookup"><span data-stu-id="6fcdd-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fcdd-109">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6fcdd-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6fcdd-110">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="6fcdd-110">Compiling the Code</span></span>  
 <span data-ttu-id="6fcdd-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6fcdd-111">This example requires:</span></span>  
  
- <span data-ttu-id="6fcdd-112">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6fcdd-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fcdd-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fcdd-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="6fcdd-114">Personalizando o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6fcdd-114">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6fcdd-115">Arquitetura de controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="6fcdd-115">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
