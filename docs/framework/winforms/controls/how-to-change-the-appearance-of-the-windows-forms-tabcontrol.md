---
title: 'Como: Alterar a aparência do TabControl do Windows Forms'
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
ms.openlocfilehash: c84ce67225b70933e65b8f88da1eaef6b1f3de99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133127"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="659c2-102">Como: Alterar a aparência do TabControl do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="659c2-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="659c2-103">Você pode alterar a aparência das guias nos Windows Forms usando propriedades do <xref:System.Windows.Forms.TabControl> e o <xref:System.Windows.Forms.TabPage> objetos que compõem guias individuais no controle.</span><span class="sxs-lookup"><span data-stu-id="659c2-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="659c2-104">Ao configurar essas propriedades, é possível exibir imagens em guias, exibir guias verticalmente em vez de horizontalmente, exibir várias linhas de guias e habilitar ou desabilitar guias com programação.</span><span class="sxs-lookup"><span data-stu-id="659c2-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="659c2-105">Exibir um ícone na parte de rótulo de uma guia</span><span class="sxs-lookup"><span data-stu-id="659c2-105">To display an icon on the label part of a tab</span></span>  
  
1.  <span data-ttu-id="659c2-106">Adicionar um <xref:System.Windows.Forms.ImageList> controle ao formulário.</span><span class="sxs-lookup"><span data-stu-id="659c2-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2.  <span data-ttu-id="659c2-107">Adicione imagens à lista de imagens.</span><span class="sxs-lookup"><span data-stu-id="659c2-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="659c2-108">Para obter mais informações sobre listas de imagens, consulte [componente ImageList](imagelist-component-windows-forms.md) e [como: Adicionar ou remover imagens com o Windows Forms componente ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="659c2-108">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3.  <span data-ttu-id="659c2-109">Defina a <xref:System.Windows.Forms.TabControl.ImageList%2A> propriedade do <xref:System.Windows.Forms.TabControl> para o <xref:System.Windows.Forms.ImageList> controle.</span><span class="sxs-lookup"><span data-stu-id="659c2-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4.  <span data-ttu-id="659c2-110">Defina a <xref:System.Windows.Forms.TabPage.ImageIndex%2A> propriedade do <xref:System.Windows.Forms.TabPage> ao índice de uma imagem apropriada na lista.</span><span class="sxs-lookup"><span data-stu-id="659c2-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="659c2-111">Criar várias linhas de guias</span><span class="sxs-lookup"><span data-stu-id="659c2-111">To create multiple rows of tabs</span></span>  
  
1.  <span data-ttu-id="659c2-112">Adicione o número de páginas de guia desejado.</span><span class="sxs-lookup"><span data-stu-id="659c2-112">Add the number of tab pages you want.</span></span>  
  
2.  <span data-ttu-id="659c2-113">Defina as <xref:System.Windows.Forms.TabControl.Multiline%2A> propriedade do <xref:System.Windows.Forms.TabControl> para `true`.</span><span class="sxs-lookup"><span data-stu-id="659c2-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3.  <span data-ttu-id="659c2-114">Se as guias não aparecem em várias linhas, defina as <xref:System.Windows.Forms.Control.Width%2A> propriedade do <xref:System.Windows.Forms.TabControl> para ser mais estreita que todas as guias.</span><span class="sxs-lookup"><span data-stu-id="659c2-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="659c2-115">Organizar as guias na lateral do controle</span><span class="sxs-lookup"><span data-stu-id="659c2-115">To arrange tabs on the side of the control</span></span>  
  
-   <span data-ttu-id="659c2-116">Defina as <xref:System.Windows.Forms.TabControl.Alignment%2A> propriedade do <xref:System.Windows.Forms.TabControl> para <xref:System.Windows.Forms.TabAlignment.Left> ou <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="659c2-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="659c2-117">Habilitar ou desabilitar todos os controles em uma guia usando programação</span><span class="sxs-lookup"><span data-stu-id="659c2-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1.  <span data-ttu-id="659c2-118">Defina as <xref:System.Windows.Forms.TabPage.Enabled%2A> propriedade do <xref:System.Windows.Forms.TabPage> para `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="659c2-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="659c2-119">Exibir guias como botões</span><span class="sxs-lookup"><span data-stu-id="659c2-119">To display tabs as buttons</span></span>  
  
-   <span data-ttu-id="659c2-120">Defina as <xref:System.Windows.Forms.TabControl.Appearance%2A> propriedade do <xref:System.Windows.Forms.TabControl> para <xref:System.Windows.Forms.TabAppearance.Buttons> ou <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="659c2-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659c2-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="659c2-121">See also</span></span>

- [<span data-ttu-id="659c2-122">Controle TabControl</span><span class="sxs-lookup"><span data-stu-id="659c2-122">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="659c2-123">Visão geral do controle TabControl</span><span class="sxs-lookup"><span data-stu-id="659c2-123">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="659c2-124">Como: Adicionar um controle a uma página da guia</span><span class="sxs-lookup"><span data-stu-id="659c2-124">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="659c2-125">Como: Desabilitar páginas de guia</span><span class="sxs-lookup"><span data-stu-id="659c2-125">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="659c2-126">Como: Adicionar e remover guias com o controle TabControl do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="659c2-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
