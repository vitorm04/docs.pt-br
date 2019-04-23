---
title: 'Como: Definir a imagem exibida por um controle do Windows Forms'
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
ms.openlocfilehash: 1de835bda5ac906837ac3fbd97b87f68f14d1953
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771524"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="3a77a-102">Como: Definir a imagem exibida por um controle do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a77a-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="3a77a-103">Vários controles de Windows Forms podem exibir imagens.</span><span class="sxs-lookup"><span data-stu-id="3a77a-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="3a77a-104">Essas imagens podem ser ícones que esclarecem o propósito de controle, como um ícone de disquete em um botão que indica a **salvar** comando.</span><span class="sxs-lookup"><span data-stu-id="3a77a-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="3a77a-105">Como alternativa, os ícones podem ser imagens de plano de fundo para dar o controle a aparência e o comportamento desejado.</span><span class="sxs-lookup"><span data-stu-id="3a77a-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="3a77a-106">Para definir a imagem exibida por um controle</span><span class="sxs-lookup"><span data-stu-id="3a77a-106">To set the image displayed by a control</span></span>  
  
1. <span data-ttu-id="3a77a-107">Defina o controle `Image` ou `BackgroundImage` propriedade em um objeto do tipo <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="3a77a-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="3a77a-108">Em geral, você será ser carregar a imagem de um arquivo usando o <xref:System.Drawing.Image.FromFile%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3a77a-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="3a77a-109">No exemplo de código a seguir, o caminho definido para o local da imagem é o **Minhas imagens** pasta.</span><span class="sxs-lookup"><span data-stu-id="3a77a-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="3a77a-110">A maioria dos computadores que executam o sistema operacional Windows vão incluir este diretório.</span><span class="sxs-lookup"><span data-stu-id="3a77a-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="3a77a-111">Isso também permite que os usuários com níveis de acesso mínimos do sistema executar o aplicativo com segurança.</span><span class="sxs-lookup"><span data-stu-id="3a77a-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="3a77a-112">O exemplo de código a seguir exige que você já tenha um formulário com um <xref:System.Windows.Forms.PictureBox> controle adicionado.</span><span class="sxs-lookup"><span data-stu-id="3a77a-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a77a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a77a-113">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
