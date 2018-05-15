---
title: Como definir a imagem exibida por um controle dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 4870f9e2acc48a90e1e2193d514926fedee05f61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="877f8-102">Como definir a imagem exibida por um controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="877f8-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="877f8-103">Vários controles de formulários do Windows podem exibir imagens.</span><span class="sxs-lookup"><span data-stu-id="877f8-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="877f8-104">Essas imagens podem ser ícones esclarecer a finalidade do controle, como um ícone de disquete em um botão denotando o **salvar** comando.</span><span class="sxs-lookup"><span data-stu-id="877f8-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="877f8-105">Como alternativa, os ícones podem ser imagens de plano de fundo para dar o controle a aparência e o comportamento desejado.</span><span class="sxs-lookup"><span data-stu-id="877f8-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="877f8-106">Para definir a imagem exibida por um controle</span><span class="sxs-lookup"><span data-stu-id="877f8-106">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="877f8-107">Definir o controle `Image` ou `BackgroundImage` propriedade para um objeto do tipo <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="877f8-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="877f8-108">Em geral, você será possível carregar a imagem de um arquivo usando o <xref:System.Drawing.Image.FromFile%2A> método.</span><span class="sxs-lookup"><span data-stu-id="877f8-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="877f8-109">No exemplo de código a seguir, o caminho definido para o local da imagem é o **Minhas imagens** pasta.</span><span class="sxs-lookup"><span data-stu-id="877f8-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="877f8-110">A maioria dos computadores que executam o sistema operacional Windows incluirá esse diretório.</span><span class="sxs-lookup"><span data-stu-id="877f8-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="877f8-111">Isso também permite que os usuários com níveis de acesso mínimos do sistema executar o aplicativo com segurança.</span><span class="sxs-lookup"><span data-stu-id="877f8-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="877f8-112">O exemplo de código a seguir exige que você já tenha um formulário com um <xref:System.Windows.Forms.PictureBox> controle adicionado.</span><span class="sxs-lookup"><span data-stu-id="877f8-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="877f8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="877f8-113">See Also</span></span>  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
