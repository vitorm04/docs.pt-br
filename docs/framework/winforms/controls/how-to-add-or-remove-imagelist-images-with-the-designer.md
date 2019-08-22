---
title: 'Como: Adicionar ou remover imagens ImageList com o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: be17d5e6a12824c1c9edc867c99e77a6a1437a36
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658591"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="e8ac1-102">Como: Adicionar ou remover imagens ImageList com o Designer</span><span class="sxs-lookup"><span data-stu-id="e8ac1-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="e8ac1-103">Você pode adicionar imagens a um <xref:System.Windows.Forms.ImageList> componente de várias maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="e8ac1-104">Você pode adicionar imagens muito rapidamente usando a marca inteligente associada <xref:System.Windows.Forms.ImageList>ao, ou se estiver definindo várias outras propriedades <xref:System.Windows.Forms.ImageList>no, talvez seja mais conveniente adicionar imagens com o janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="e8ac1-105">Também é possível adicionar imagens usando o código.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-105">You can also add images by using code.</span></span> <span data-ttu-id="e8ac1-106">Para obter mais informações sobre como adicionar imagens com código, consulte [como: Adicionar ou remover imagens com o componente](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)Windows Forms ImageList.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="e8ac1-107">Normalmente, você preenche <xref:System.Windows.Forms.ImageList> o componente com imagens antes que ele seja associado a um controle, mas isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="e8ac1-108">Para adicionar ou remover imagens usando a janela Propriedades</span><span class="sxs-lookup"><span data-stu-id="e8ac1-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="e8ac1-109">Selecione o <xref:System.Windows.Forms.ImageList> componente ou adicione um ao formulário.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="e8ac1-110">Na janela Propriedades, clique no botão de reticências![(o botão de reticências (...) na janela Propriedades do Visual](./media/visual-studio-ellipsis-button.png)Studio.) ao <xref:System.Windows.Forms.ImageList.Images%2A> lado da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="e8ac1-111">No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="e8ac1-112">Para adicionar ou remover imagens usando a smart tag</span><span class="sxs-lookup"><span data-stu-id="e8ac1-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="e8ac1-113">Selecione o <xref:System.Windows.Forms.ImageList> componente ou adicione um ao formulário.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="e8ac1-114">Clique no glifo de smart tag (![Glifo de smart tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="e8ac1-114">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>

3. <span data-ttu-id="e8ac1-115">Na caixa de diálogo **Tarefas ImageList**, selecione **Escolher imagens**.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-115">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="e8ac1-116">No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.</span><span class="sxs-lookup"><span data-stu-id="e8ac1-116">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8ac1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8ac1-117">See also</span></span>

- [<span data-ttu-id="e8ac1-118">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="e8ac1-118">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="e8ac1-119">Passo a passo: Executando tarefas comuns usando marcas inteligentes em controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8ac1-119">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="e8ac1-120">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="e8ac1-120">ImageList Component</span></span>](imagelist-component-windows-forms.md)
