---
title: 'Como: Modificar o tamanho ou a colocação de uma imagem em tempo de execução (Windows Forms)'
ms.date: 03/30/2017
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
ms.openlocfilehash: 5d817d34e47253b2e35afa7bb41c59eea06e1f94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178822"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="3a40c-102">Como: Modificar o tamanho ou a colocação de uma imagem em tempo de execução (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3a40c-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="3a40c-103">Se você usar o Windows Forms <xref:System.Windows.Forms.PictureBox> controle em um formulário, você pode definir o <xref:System.Windows.Forms.PictureBox.SizeMode%2A> propriedade nele para:</span><span class="sxs-lookup"><span data-stu-id="3a40c-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="3a40c-104">Alinhe o canto superior esquerdo da imagem com o canto superior esquerdo do controle</span><span class="sxs-lookup"><span data-stu-id="3a40c-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="3a40c-105">Centralize a imagem no controle</span><span class="sxs-lookup"><span data-stu-id="3a40c-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="3a40c-106">Ajuste o tamanho do controle para se adaptar à imagem exibida</span><span class="sxs-lookup"><span data-stu-id="3a40c-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="3a40c-107">Alongue qualquer imagem exibida para se ajustar ao controle</span><span class="sxs-lookup"><span data-stu-id="3a40c-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="3a40c-108">Ampliar uma imagem (especialmente em formato bitmap) pode causar perda na qualidade.</span><span class="sxs-lookup"><span data-stu-id="3a40c-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="3a40c-109">Metarquivos, que são listas de instruções gráficas para desenho de imagens em tempo de execução, são mais adequados para ampliar do que os bitmaps.</span><span class="sxs-lookup"><span data-stu-id="3a40c-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="3a40c-110">Para definir a propriedade SizeMode em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3a40c-110">To set the SizeMode property at run time</span></span>  
  
1.  <span data-ttu-id="3a40c-111">Definir <xref:System.Windows.Forms.PictureBox.SizeMode%2A> à <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (o padrão), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, ou <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="3a40c-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> <span data-ttu-id="3a40c-112">significa que a imagem é colocada no canto superior esquerdo do controle; Se a imagem for maior que o controle, suas bordas inferiores e direita serão cortadas.</span><span class="sxs-lookup"><span data-stu-id="3a40c-112">means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> <span data-ttu-id="3a40c-113">significa que a imagem é centralizada no controle; Se a imagem for maior que o controle, as bordas exteriores serão cortadas.</span><span class="sxs-lookup"><span data-stu-id="3a40c-113">means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> <span data-ttu-id="3a40c-114">significa que o tamanho do controle é ajustado para o tamanho da imagem.</span><span class="sxs-lookup"><span data-stu-id="3a40c-114">means that the size of the control is adjusted to the size of the image.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> <span data-ttu-id="3a40c-115">é o inverso e significa que o tamanho da imagem é ajustado para o tamanho do controle.</span><span class="sxs-lookup"><span data-stu-id="3a40c-115">is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="3a40c-116">No exemplo abaixo, o caminho definido para o local da imagem é a pasta Meus Documentos.</span><span class="sxs-lookup"><span data-stu-id="3a40c-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="3a40c-117">Isso acontece porque presumimos que a maioria dos computadores rodando o sistema operacional Windows vai incluir este diretório.</span><span class="sxs-lookup"><span data-stu-id="3a40c-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="3a40c-118">Isso também permite que usuários com níveis mínimos de acesso ao sistema executem com segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a40c-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="3a40c-119">O exemplo a seguir supõe um formulário com um <xref:System.Windows.Forms.PictureBox> controle já adicionado.</span><span class="sxs-lookup"><span data-stu-id="3a40c-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a40c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a40c-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="3a40c-121">Como: Carregar uma imagem usando o designer</span><span class="sxs-lookup"><span data-stu-id="3a40c-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="3a40c-122">Visão geral do controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="3a40c-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="3a40c-123">Como: Definir imagens em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3a40c-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="3a40c-124">Controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="3a40c-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
