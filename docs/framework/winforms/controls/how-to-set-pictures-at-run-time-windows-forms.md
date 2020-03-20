---
title: Como definir imagens em tempo de execução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: cd599ac7e07b5210f8bcff1ffbc76b3d9ee563d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182110"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="569ee-102">Como definir imagens em tempo de execução (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="569ee-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="569ee-103">Você pode definir programáticamente a imagem <xref:System.Windows.Forms.PictureBox> exibida por um controle do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="569ee-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="569ee-104">Para definir uma imagem programática</span><span class="sxs-lookup"><span data-stu-id="569ee-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="569ee-105">Defina <xref:System.Windows.Forms.PictureBox.Image%2A> a <xref:System.Drawing.Image.FromFile%2A> propriedade usando <xref:System.Drawing.Image> o método da classe.</span><span class="sxs-lookup"><span data-stu-id="569ee-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="569ee-106">No exemplo abaixo, o caminho definido para o local da imagem é a pasta Meus Documentos.</span><span class="sxs-lookup"><span data-stu-id="569ee-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="569ee-107">Isso acontece porque presumimos que a maioria dos computadores rodando o sistema operacional Windows vai incluir este diretório.</span><span class="sxs-lookup"><span data-stu-id="569ee-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="569ee-108">Isso também permite que usuários com níveis mínimos de acesso ao sistema executem com segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="569ee-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="569ee-109">O exemplo abaixo assume um <xref:System.Windows.Forms.PictureBox> formulário com um controle já adicionado.</span><span class="sxs-lookup"><span data-stu-id="569ee-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="569ee-110">Para limpar um gráfico</span><span class="sxs-lookup"><span data-stu-id="569ee-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="569ee-111">Primeiro, libere a memória que está sendo usada pela imagem e, em seguida, limpe o gráfico.</span><span class="sxs-lookup"><span data-stu-id="569ee-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="569ee-112">A coleta de lixo liberará a memória mais tarde se o gerenciamento da memória se tornar um problema.</span><span class="sxs-lookup"><span data-stu-id="569ee-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="569ee-113">Para obter mais informações sobre <xref:System.Drawing.Image.Dispose%2A> por que você deve usar o método desta forma, consulte [Limpar recursos não gerenciados](../../../standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="569ee-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="569ee-114">Este código limpará a imagem mesmo que um gráfico tenha sido carregado no controle na hora do design.</span><span class="sxs-lookup"><span data-stu-id="569ee-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="569ee-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="569ee-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="569ee-116">Visão geral do controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="569ee-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="569ee-117">Como carregar uma imagem usando o designer</span><span class="sxs-lookup"><span data-stu-id="569ee-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="569ee-118">Como modificar o tamanho ou a colocação de uma imagem em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="569ee-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="569ee-119">Controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="569ee-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
