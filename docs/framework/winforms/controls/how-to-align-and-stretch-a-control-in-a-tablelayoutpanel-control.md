---
title: Como alinhar e alongar um controle em um controle TableLayoutPanel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 043adb68b88ab031cea3de1206d1f2c4252b75d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="122a5-102">Como alinhar e alongar um controle em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="122a5-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>
<span data-ttu-id="122a5-103">Você pode alinhar e Alongar controles em um <xref:System.Windows.Forms.TableLayoutPanel> com o <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="122a5-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="122a5-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="122a5-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="122a5-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="122a5-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="122a5-106">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="122a5-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-align-and-stretch-a-control"></a><span data-ttu-id="122a5-107">Para alinhar e alongar um controle</span><span class="sxs-lookup"><span data-stu-id="122a5-107">To align and stretch a control</span></span>  
  
1.  <span data-ttu-id="122a5-108">Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="122a5-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="122a5-109">Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** na célula superior esquerda do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="122a5-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="122a5-110">O <xref:System.Windows.Forms.Button> controle é centralizado na célula.</span><span class="sxs-lookup"><span data-stu-id="122a5-110">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>  
  
3.  <span data-ttu-id="122a5-111">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left,Right`.</span><span class="sxs-lookup"><span data-stu-id="122a5-111">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="122a5-112">O <xref:System.Windows.Forms.Button> controlar expande para corresponder à largura da célula.</span><span class="sxs-lookup"><span data-stu-id="122a5-112">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>  
  
4.  <span data-ttu-id="122a5-113">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top,Bottom`.</span><span class="sxs-lookup"><span data-stu-id="122a5-113">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="122a5-114">O <xref:System.Windows.Forms.Button> controlar expande para corresponder a altura da célula.</span><span class="sxs-lookup"><span data-stu-id="122a5-114">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>  
  
5.  <span data-ttu-id="122a5-115">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="122a5-115">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="122a5-116">O <xref:System.Windows.Forms.Button> controle se expande para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="122a5-116">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>  
  
6.  <span data-ttu-id="122a5-117">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="122a5-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="122a5-118">O <xref:System.Windows.Forms.Button> controle retorna ao tamanho original e move para o canto superior esquerdo da célula.</span><span class="sxs-lookup"><span data-stu-id="122a5-118">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="122a5-119">O **Windows Forms Designer** definiu o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="122a5-119">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>  
  
7.  <span data-ttu-id="122a5-120">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Bottom,Right`.</span><span class="sxs-lookup"><span data-stu-id="122a5-120">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="122a5-121">O <xref:System.Windows.Forms.Button> move o controle para o canto inferior direito da célula.</span><span class="sxs-lookup"><span data-stu-id="122a5-121">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>  
  
8.  <span data-ttu-id="122a5-122">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade <xref:System.Windows.Forms.AnchorStyles.None>.</span><span class="sxs-lookup"><span data-stu-id="122a5-122">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="122a5-123">O <xref:System.Windows.Forms.Button> move o controle para o centro da célula.</span><span class="sxs-lookup"><span data-stu-id="122a5-123">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122a5-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="122a5-124">See Also</span></span>  
 [<span data-ttu-id="122a5-125">Controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="122a5-125">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
