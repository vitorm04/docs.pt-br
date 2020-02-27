---
title: Como adicionar ou remover imagens ImageList com o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628716"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="47e9e-102">Como adicionar ou remover imagens ImageList com o designer</span><span class="sxs-lookup"><span data-stu-id="47e9e-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="47e9e-103">Você pode adicionar imagens a um componente de <xref:System.Windows.Forms.ImageList> várias maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="47e9e-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="47e9e-104">Você pode adicionar imagens muito rapidamente usando a marca inteligente associada à <xref:System.Windows.Forms.ImageList>, ou se estiver definindo várias outras propriedades na <xref:System.Windows.Forms.ImageList>, talvez seja mais conveniente adicionar imagens com o janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="47e9e-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="47e9e-105">Também é possível adicionar imagens usando o código.</span><span class="sxs-lookup"><span data-stu-id="47e9e-105">You can also add images by using code.</span></span> <span data-ttu-id="47e9e-106">Para obter mais informações sobre como adicionar imagens com o código, consulte [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="47e9e-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="47e9e-107">Normalmente, você preenche o componente <xref:System.Windows.Forms.ImageList> com imagens antes que ele seja associado a um controle, mas isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="47e9e-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="47e9e-108">Para adicionar ou remover imagens usando a janela Propriedades</span><span class="sxs-lookup"><span data-stu-id="47e9e-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="47e9e-109">Selecione o componente <xref:System.Windows.Forms.ImageList> ou adicione um ao formulário.</span><span class="sxs-lookup"><span data-stu-id="47e9e-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="47e9e-110">Na janela Propriedades, clique no botão de reticências (![o botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ImageList.Images%2A>.</span><span class="sxs-lookup"><span data-stu-id="47e9e-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="47e9e-111">No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.</span><span class="sxs-lookup"><span data-stu-id="47e9e-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="47e9e-112">Para adicionar ou remover imagens usando a smart tag</span><span class="sxs-lookup"><span data-stu-id="47e9e-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="47e9e-113">Selecione o componente <xref:System.Windows.Forms.ImageList> ou adicione um ao formulário.</span><span class="sxs-lookup"><span data-stu-id="47e9e-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="47e9e-114">Clique no glifo ações do designer (</span><span class="sxs-lookup"><span data-stu-id="47e9e-114">Click the designer actions glyph (</span></span>![Pequena seta preta](./media/designer-actions-glyph.gif)<span data-ttu-id="47e9e-116">)</span><span class="sxs-lookup"><span data-stu-id="47e9e-116">)</span></span>

3. <span data-ttu-id="47e9e-117">Na caixa de diálogo **Tarefas ImageList**, selecione **Escolher imagens**.</span><span class="sxs-lookup"><span data-stu-id="47e9e-117">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="47e9e-118">No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.</span><span class="sxs-lookup"><span data-stu-id="47e9e-118">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="47e9e-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="47e9e-119">See also</span></span>

- [<span data-ttu-id="47e9e-120">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="47e9e-120">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="47e9e-121">Walkthrough: executar tarefas comuns usando ações de designer</span><span class="sxs-lookup"><span data-stu-id="47e9e-121">Walkthrough: Perform common tasks using designer actions</span></span>](perform-common-tasks-design-actions.md)
- [<span data-ttu-id="47e9e-122">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="47e9e-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
