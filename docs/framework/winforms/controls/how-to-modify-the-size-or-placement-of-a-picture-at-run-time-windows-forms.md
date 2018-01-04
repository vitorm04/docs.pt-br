---
title: "Como modificar o tamanho ou a colocação de uma imagem em tempo de execução (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e02ea1cbcb1fdd86d182bfba23241acb91c4b54a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="5e0ed-102">Como modificar o tamanho ou a colocação de uma imagem em tempo de execução (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5e0ed-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="5e0ed-103">Se você usar o Windows Forms <xref:System.Windows.Forms.PictureBox> controle em um formulário, você pode definir o <xref:System.Windows.Forms.PictureBox.SizeMode%2A> propriedade nele para:</span><span class="sxs-lookup"><span data-stu-id="5e0ed-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="5e0ed-104">Alinhe o canto superior esquerdo da imagem com o canto superior esquerdo do controle</span><span class="sxs-lookup"><span data-stu-id="5e0ed-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="5e0ed-105">Centralize a imagem no controle</span><span class="sxs-lookup"><span data-stu-id="5e0ed-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="5e0ed-106">Ajuste o tamanho do controle para se adaptar à imagem exibida</span><span class="sxs-lookup"><span data-stu-id="5e0ed-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="5e0ed-107">Alongue qualquer imagem exibida para se ajustar ao controle</span><span class="sxs-lookup"><span data-stu-id="5e0ed-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="5e0ed-108">Ampliar uma imagem (especialmente em formato bitmap) pode causar perda na qualidade.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="5e0ed-109">Metarquivos, que são listas de instruções gráficas para desenho de imagens em tempo de execução, são mais adequados para ampliar do que os bitmaps.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="5e0ed-110">Para definir a propriedade SizeMode em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5e0ed-110">To set the SizeMode property at run time</span></span>  
  
1.  <span data-ttu-id="5e0ed-111">Definir <xref:System.Windows.Forms.PictureBox.SizeMode%2A> para <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (o padrão), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, ou <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="5e0ed-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>significa que a imagem é colocada no canto de superior esquerdo do controle; Se a imagem for maior do que o controle, bordas inferiores e direita são cortadas.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="5e0ed-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>significa que a imagem é centralizada dentro do controle; Se a imagem for maior do que o controle, bordas externas da imagem são cortadas.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="5e0ed-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>significa que o tamanho do controle é ajustado para o tamanho da imagem.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="5e0ed-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>é o inverso e significa que o tamanho da imagem é ajustado para o tamanho do controle.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="5e0ed-116">No exemplo abaixo, o caminho definido para o local da imagem é a pasta Meus Documentos.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="5e0ed-117">Isso acontece porque presumimos que a maioria dos computadores rodando o sistema operacional Windows vai incluir este diretório.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="5e0ed-118">Isso também permite que usuários com níveis mínimos de acesso ao sistema executem com segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="5e0ed-119">O exemplo a seguir assume uma forma com um <xref:System.Windows.Forms.PictureBox> controle já foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="5e0ed-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5e0ed-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e0ed-120">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="5e0ed-121">Como carregar uma imagem usando o designer</span><span class="sxs-lookup"><span data-stu-id="5e0ed-121">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [<span data-ttu-id="5e0ed-122">Visão geral do controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="5e0ed-122">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="5e0ed-123">Como definir imagens em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5e0ed-123">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="5e0ed-124">Controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="5e0ed-124">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
