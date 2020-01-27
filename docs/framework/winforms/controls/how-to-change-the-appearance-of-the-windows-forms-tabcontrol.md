---
title: Alterar a aparência do TabControl
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746618"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="c5560-102">Como alterar a aparência do TabControl dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5560-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="c5560-103">Você pode alterar a aparência das guias em Windows Forms usando as propriedades do <xref:System.Windows.Forms.TabControl> e os objetos <xref:System.Windows.Forms.TabPage> que compõem as guias individuais do controle.</span><span class="sxs-lookup"><span data-stu-id="c5560-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="c5560-104">Ao configurar essas propriedades, é possível exibir imagens em guias, exibir guias verticalmente em vez de horizontalmente, exibir várias linhas de guias e habilitar ou desabilitar guias com programação.</span><span class="sxs-lookup"><span data-stu-id="c5560-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="c5560-105">Exibir um ícone na parte de rótulo de uma guia</span><span class="sxs-lookup"><span data-stu-id="c5560-105">To display an icon on the label part of a tab</span></span>  
  
1. <span data-ttu-id="c5560-106">Adicione um controle de <xref:System.Windows.Forms.ImageList> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="c5560-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2. <span data-ttu-id="c5560-107">Adicione imagens à lista de imagens.</span><span class="sxs-lookup"><span data-stu-id="c5560-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="c5560-108">Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="c5560-108">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3. <span data-ttu-id="c5560-109">Defina a propriedade <xref:System.Windows.Forms.TabControl.ImageList%2A> do <xref:System.Windows.Forms.TabControl> para o controle de <xref:System.Windows.Forms.ImageList>.</span><span class="sxs-lookup"><span data-stu-id="c5560-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4. <span data-ttu-id="c5560-110">Defina a propriedade <xref:System.Windows.Forms.TabPage.ImageIndex%2A> do <xref:System.Windows.Forms.TabPage> como o índice de uma imagem apropriada na lista.</span><span class="sxs-lookup"><span data-stu-id="c5560-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="c5560-111">Criar várias linhas de guias</span><span class="sxs-lookup"><span data-stu-id="c5560-111">To create multiple rows of tabs</span></span>  
  
1. <span data-ttu-id="c5560-112">Adicione o número de páginas de guia desejado.</span><span class="sxs-lookup"><span data-stu-id="c5560-112">Add the number of tab pages you want.</span></span>  
  
2. <span data-ttu-id="c5560-113">Defina a propriedade <xref:System.Windows.Forms.TabControl.Multiline%2A> da <xref:System.Windows.Forms.TabControl> como `true`.</span><span class="sxs-lookup"><span data-stu-id="c5560-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3. <span data-ttu-id="c5560-114">Se as guias ainda não aparecerem em várias linhas, defina a propriedade <xref:System.Windows.Forms.Control.Width%2A> da <xref:System.Windows.Forms.TabControl> como mais estreita do que todas as guias.</span><span class="sxs-lookup"><span data-stu-id="c5560-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="c5560-115">Organizar as guias na lateral do controle</span><span class="sxs-lookup"><span data-stu-id="c5560-115">To arrange tabs on the side of the control</span></span>  
  
- <span data-ttu-id="c5560-116">Defina a propriedade <xref:System.Windows.Forms.TabControl.Alignment%2A> da <xref:System.Windows.Forms.TabControl> como <xref:System.Windows.Forms.TabAlignment.Left> ou <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="c5560-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="c5560-117">Habilitar ou desabilitar todos os controles em uma guia usando programação</span><span class="sxs-lookup"><span data-stu-id="c5560-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1. <span data-ttu-id="c5560-118">Defina a propriedade <xref:System.Windows.Forms.TabPage.Enabled%2A> da <xref:System.Windows.Forms.TabPage> como `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="c5560-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="c5560-119">Exibir guias como botões</span><span class="sxs-lookup"><span data-stu-id="c5560-119">To display tabs as buttons</span></span>  
  
- <span data-ttu-id="c5560-120">Defina a propriedade <xref:System.Windows.Forms.TabControl.Appearance%2A> da <xref:System.Windows.Forms.TabControl> como <xref:System.Windows.Forms.TabAppearance.Buttons> ou <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="c5560-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5560-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="c5560-121">See also</span></span>

- [<span data-ttu-id="c5560-122">Controle TabControl</span><span class="sxs-lookup"><span data-stu-id="c5560-122">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="c5560-123">Visão geral do controle TabControl</span><span class="sxs-lookup"><span data-stu-id="c5560-123">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="c5560-124">Como adicionar um controle a uma página da guia</span><span class="sxs-lookup"><span data-stu-id="c5560-124">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="c5560-125">Como desabilitar páginas de guia</span><span class="sxs-lookup"><span data-stu-id="c5560-125">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="c5560-126">Como adicionar e remover guias com o TabControl dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5560-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
