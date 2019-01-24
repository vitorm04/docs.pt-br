---
title: 'Como: Adicionar ou remover imagens com o componente ImageList dos Windows Forms'
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
ms.openlocfilehash: a81cf11ea5ca405e2013b7c7375a863aeb1f110f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609610"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Como: Adicionar ou remover imagens com o componente ImageList dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.ImageList> componente normalmente é preenchido com imagens antes que ele seja associado a um controle. No entanto, você pode adicionar e remover imagens depois de associar a lista de imagens a um controle.  
  
> [!NOTE]
>  Quando você remove imagens, verifique o <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> propriedade de qualquer controle associado ainda é válida.  
  
### <a name="to-add-images-programmatically"></a>Para adicionar imagens de forma programática  
  
-   Use o <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> método da lista de imagens <xref:System.Windows.Forms.ImageList.Images%2A> propriedade.  
  
     No exemplo de código a seguir, o caminho definido para o local da imagem é a pasta **Meus documentos**. Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta. Escolher esse local também permite que os usuários que têm níveis de acesso ao sistema mínimos executem com mais segurança o aplicativo. O exemplo de código a seguir exige que você tenha um formulário com um <xref:System.Windows.Forms.ImageList> controle já adicionado.  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>Para adicionar imagens com um valor de chave.  
  
-   Use um dos <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> métodos da lista de imagens <xref:System.Windows.Forms.ImageList.Images%2A> propriedade que aceita um valor de chave.  
  
     No exemplo de código a seguir, o caminho definido para o local da imagem é a pasta **Meus documentos**. Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta. Escolher esse local também permite que os usuários que têm níveis de acesso ao sistema mínimos executem com mais segurança o aplicativo. O exemplo de código a seguir exige que você tenha um formulário com um <xref:System.Windows.Forms.ImageList> controle já adicionado.  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>Para remover todas as imagens de forma programática  
  
-   Use o <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> método para remover uma única imagem  
  
     ,-ou-  
  
     Use o <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> método para limpar todas as imagens na lista de imagens.  
  
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
  
### <a name="to-remove-images-by-key"></a>Para remover imagens por chave  
  
-   Use o <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> método para remover uma única imagem por sua chave.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Consulte também
- [Componente ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
- [Visão geral do componente ImageList](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)
- [Imagens, bitmaps e metarquivos](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
