---
title: Como adicionar ou remover imagens ImageList com o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: c85e55b6aef45eea65e6f82269375f80acf71017
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="57a2f-102">Como adicionar ou remover imagens ImageList com o designer</span><span class="sxs-lookup"><span data-stu-id="57a2f-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="57a2f-103">Você pode adicionar imagens a um <xref:System.Windows.Forms.ImageList> componente várias maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="57a2f-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="57a2f-104">Você pode adicionar imagens muito rapidamente, usando a marca inteligente associada a <xref:System.Windows.Forms.ImageList>, ou se você estiver configurando várias outras propriedades da <xref:System.Windows.Forms.ImageList>, você pode achar mais conveniente adicionar imagens com a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="57a2f-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="57a2f-105">Também é possível adicionar imagens usando o código.</span><span class="sxs-lookup"><span data-stu-id="57a2f-105">You can also add images by using code.</span></span> <span data-ttu-id="57a2f-106">Para obter mais informações sobre como adicionar imagens com o código, consulte [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="57a2f-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="57a2f-107">Normalmente você preencher o <xref:System.Windows.Forms.ImageList> componente com imagens antes que ele está associado com um controle, mas isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="57a2f-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57a2f-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="57a2f-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="57a2f-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="57a2f-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="57a2f-110">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="57a2f-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="57a2f-111">Para adicionar ou remover imagens usando a janela Propriedades</span><span class="sxs-lookup"><span data-stu-id="57a2f-111">To add or remove images by using the Properties window</span></span>  
  
1.  <span data-ttu-id="57a2f-112">Selecione o <xref:System.Windows.Forms.ImageList> componente, ou adicione um para o formulário.</span><span class="sxs-lookup"><span data-stu-id="57a2f-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="57a2f-113">Na janela Propriedades, clique no botão de reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.ImageList.Images%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="57a2f-113">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3.  <span data-ttu-id="57a2f-114">No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.</span><span class="sxs-lookup"><span data-stu-id="57a2f-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="57a2f-115">Para adicionar ou remover imagens usando a smart tag</span><span class="sxs-lookup"><span data-stu-id="57a2f-115">To add or remove images using the smart tag</span></span>  
  
1.  <span data-ttu-id="57a2f-116">Selecione o <xref:System.Windows.Forms.ImageList> componente, ou adicione um para o formulário.</span><span class="sxs-lookup"><span data-stu-id="57a2f-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="57a2f-117">Clique no glifo de smart tag (![Glifo de smart tag](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="57a2f-117">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3.  <span data-ttu-id="57a2f-118">Na caixa de diálogo **Tarefas ImageList**, selecione **Escolher imagens**.</span><span class="sxs-lookup"><span data-stu-id="57a2f-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4.  <span data-ttu-id="57a2f-119">No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.</span><span class="sxs-lookup"><span data-stu-id="57a2f-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a2f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57a2f-120">See Also</span></span>  
 [<span data-ttu-id="57a2f-121">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="57a2f-121">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="57a2f-122">Passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57a2f-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 [<span data-ttu-id="57a2f-123">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="57a2f-123">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
