---
title: 'Como: Adicionar ou remover imagens com o componente ImageList do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
ms.openlocfilehash: 286b56cddc18589b936a7f053a12ed44c81a32b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072968"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="18a6b-102">Como: Adicionar ou remover imagens com o componente ImageList do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18a6b-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="18a6b-103">Os formulários do Windows <xref:System.Windows.Forms.ImageList> componente normalmente é preenchido com imagens antes que ele seja associado a um controle.</span><span class="sxs-lookup"><span data-stu-id="18a6b-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="18a6b-104">No entanto, você pode adicionar e remover imagens depois de associar a lista de imagens a um controle.</span><span class="sxs-lookup"><span data-stu-id="18a6b-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18a6b-105">Quando você remove imagens, verifique o <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> propriedade de qualquer controle associado ainda é válida.</span><span class="sxs-lookup"><span data-stu-id="18a6b-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="18a6b-106">Para adicionar imagens de forma programática</span><span class="sxs-lookup"><span data-stu-id="18a6b-106">To add images programmatically</span></span>  
  
-   <span data-ttu-id="18a6b-107">Use o <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> método da lista de imagens <xref:System.Windows.Forms.ImageList.Images%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="18a6b-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="18a6b-108">No exemplo de código a seguir, o caminho definido para o local da imagem é a pasta **Meus documentos**.</span><span class="sxs-lookup"><span data-stu-id="18a6b-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="18a6b-109">Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta.</span><span class="sxs-lookup"><span data-stu-id="18a6b-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="18a6b-110">Escolher esse local também permite que os usuários que têm níveis de acesso ao sistema mínimos executem com mais segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18a6b-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="18a6b-111">O exemplo de código a seguir exige que você tenha um formulário com um <xref:System.Windows.Forms.ImageList> controle já adicionado.</span><span class="sxs-lookup"><span data-stu-id="18a6b-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the   
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =   
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample   
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as   
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =   
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="18a6b-112">Para adicionar imagens com um valor de chave.</span><span class="sxs-lookup"><span data-stu-id="18a6b-112">To add images with a key value.</span></span>  
  
-   <span data-ttu-id="18a6b-113">Use um dos <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> métodos da lista de imagens <xref:System.Windows.Forms.ImageList.Images%2A> propriedade que aceita um valor de chave.</span><span class="sxs-lookup"><span data-stu-id="18a6b-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="18a6b-114">No exemplo de código a seguir, o caminho definido para o local da imagem é a pasta **Meus documentos**.</span><span class="sxs-lookup"><span data-stu-id="18a6b-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="18a6b-115">Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta.</span><span class="sxs-lookup"><span data-stu-id="18a6b-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="18a6b-116">Escolher esse local também permite que os usuários que têm níveis de acesso ao sistema mínimos executem com mais segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18a6b-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="18a6b-117">O exemplo de código a seguir exige que você tenha um formulário com um <xref:System.Windows.Forms.ImageList> controle já adicionado.</span><span class="sxs-lookup"><span data-stu-id="18a6b-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the   
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =   
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
```  
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="18a6b-118">Para remover todas as imagens de forma programática</span><span class="sxs-lookup"><span data-stu-id="18a6b-118">To remove all images programmatically</span></span>  
  
-   <span data-ttu-id="18a6b-119">Use o <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> método para remover uma única imagem</span><span class="sxs-lookup"><span data-stu-id="18a6b-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="18a6b-120">,-ou-</span><span class="sxs-lookup"><span data-stu-id="18a6b-120">,-or-</span></span>  
  
     <span data-ttu-id="18a6b-121">Use o <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> método para limpar todas as imagens na lista de imagens.</span><span class="sxs-lookup"><span data-stu-id="18a6b-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
```  
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="18a6b-122">Para remover imagens por chave</span><span class="sxs-lookup"><span data-stu-id="18a6b-122">To remove images by key</span></span>  
  
-   <span data-ttu-id="18a6b-123">Use o <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> método para remover uma única imagem por sua chave.</span><span class="sxs-lookup"><span data-stu-id="18a6b-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="18a6b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18a6b-124">See also</span></span>

- [<span data-ttu-id="18a6b-125">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="18a6b-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="18a6b-126">Visão geral do componente ImageList</span><span class="sxs-lookup"><span data-stu-id="18a6b-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="18a6b-127">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="18a6b-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
