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
ms.openlocfilehash: 99bde4fac7b3057358c7e6a8550efdb4cc351eb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037875"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="d8e6d-102">Como: Definir a imagem exibida por um controle de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8e6d-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="d8e6d-103">Vários controles de Windows Forms podem exibir imagens.</span><span class="sxs-lookup"><span data-stu-id="d8e6d-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="d8e6d-104">Essas imagens podem ser ícones que esclarecem a finalidade do controle, como um ícone de disquete em um botão que indica o comando **salvar** .</span><span class="sxs-lookup"><span data-stu-id="d8e6d-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="d8e6d-105">Como alternativa, os ícones podem ser imagens de plano de fundo para dar ao controle a aparência e o comportamento que você deseja.</span><span class="sxs-lookup"><span data-stu-id="d8e6d-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="d8e6d-106">Para definir a imagem exibida por um controle</span><span class="sxs-lookup"><span data-stu-id="d8e6d-106">To set the image displayed by a control</span></span>

1. <span data-ttu-id="d8e6d-107">Defina a propriedade `Image` ou `BackgroundImage` o controle como um objeto do tipo <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="d8e6d-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="d8e6d-108">Em geral, você carregará a imagem de um arquivo usando o <xref:System.Drawing.Image.FromFile%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d8e6d-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

     <span data-ttu-id="d8e6d-109">No exemplo de código a seguir, o caminho definido para o local da imagem é a pasta **minhas imagens** .</span><span class="sxs-lookup"><span data-stu-id="d8e6d-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="d8e6d-110">A maioria dos computadores que executam o sistema operacional Windows incluirá esse diretório.</span><span class="sxs-lookup"><span data-stu-id="d8e6d-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="d8e6d-111">Isso também permite que os usuários com níveis mínimos de acesso do sistema executem o aplicativo com segurança.</span><span class="sxs-lookup"><span data-stu-id="d8e6d-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="d8e6d-112">O exemplo de código a seguir requer que você já tenha um formulário <xref:System.Windows.Forms.PictureBox> com um controle adicionado.</span><span class="sxs-lookup"><span data-stu-id="d8e6d-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d8e6d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8e6d-113">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
