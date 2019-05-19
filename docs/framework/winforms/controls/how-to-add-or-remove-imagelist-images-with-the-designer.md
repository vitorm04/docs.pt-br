---
title: 'Como: Adicionar ou remover imagens ImageList com o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 346d7107c9c17c5df06fa0e47f7a35355344f590
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880730"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="608cb-102">Como: Adicionar ou remover imagens ImageList com o Designer</span><span class="sxs-lookup"><span data-stu-id="608cb-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="608cb-103">Você pode adicionar imagens a um <xref:System.Windows.Forms.ImageList> componente de várias maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="608cb-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="608cb-104">Você pode adicionar imagens rapidamente usando a smart tag associada a <xref:System.Windows.Forms.ImageList>, ou se você estiver configurando várias outras propriedades do <xref:System.Windows.Forms.ImageList>, talvez seja mais conveniente para adicionar imagens com a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="608cb-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="608cb-105">Também é possível adicionar imagens usando o código.</span><span class="sxs-lookup"><span data-stu-id="608cb-105">You can also add images by using code.</span></span> <span data-ttu-id="608cb-106">Para obter mais informações sobre como adicionar imagens com o código, consulte [como: Adicionar ou remover imagens com o Windows Forms componente ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="608cb-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="608cb-107">Normalmente, você preenche o <xref:System.Windows.Forms.ImageList> componente com imagens antes que ele está associado com um controle, mas isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="608cb-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="608cb-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="608cb-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="608cb-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="608cb-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="608cb-110">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="608cb-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="608cb-111">Para adicionar ou remover imagens usando a janela Propriedades</span><span class="sxs-lookup"><span data-stu-id="608cb-111">To add or remove images by using the Properties window</span></span>  
  
1. <span data-ttu-id="608cb-112">Selecione o <xref:System.Windows.Forms.ImageList> componente, ou adicionar um ao formulário.</span><span class="sxs-lookup"><span data-stu-id="608cb-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="608cb-113">Na janela Propriedades, clique no botão de reticências (![botão do botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado de <xref:System.Windows.Forms.ImageList.Images%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="608cb-113">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3. <span data-ttu-id="608cb-114">No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.</span><span class="sxs-lookup"><span data-stu-id="608cb-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="608cb-115">Para adicionar ou remover imagens usando a smart tag</span><span class="sxs-lookup"><span data-stu-id="608cb-115">To add or remove images using the smart tag</span></span>  
  
1. <span data-ttu-id="608cb-116">Selecione o <xref:System.Windows.Forms.ImageList> componente, ou adicionar um ao formulário.</span><span class="sxs-lookup"><span data-stu-id="608cb-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2. <span data-ttu-id="608cb-117">Clique no glifo de smart tag (![Glifo de smart tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="608cb-117">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3. <span data-ttu-id="608cb-118">Na caixa de diálogo **Tarefas ImageList**, selecione **Escolher imagens**.</span><span class="sxs-lookup"><span data-stu-id="608cb-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4. <span data-ttu-id="608cb-119">No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.</span><span class="sxs-lookup"><span data-stu-id="608cb-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608cb-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="608cb-120">See also</span></span>

- [<span data-ttu-id="608cb-121">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="608cb-121">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="608cb-122">Passo a passo: Realizando tarefas comuns usando Smart Tags no Windows, controles de formulários</span><span class="sxs-lookup"><span data-stu-id="608cb-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="608cb-123">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="608cb-123">ImageList Component</span></span>](imagelist-component-windows-forms.md)
