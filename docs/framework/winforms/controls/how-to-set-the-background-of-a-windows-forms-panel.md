---
title: 'Como: Definir plano de fundo de um painel do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: 1c4eadaadf561e127ac2eaa87f62aea4e1dc7ea4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636073"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="d32d6-102">Como: Definir plano de fundo de um painel do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d32d6-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="d32d6-103">Um Windows Forms <xref:System.Windows.Forms.Panel> controle pode exibir uma cor de fundo e uma imagem de plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="d32d6-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="d32d6-104">O <xref:System.Windows.Forms.Control.BackColor%2A> propriedade define a cor de plano de fundo de controles contidos, como rótulos e botões de opção.</span><span class="sxs-lookup"><span data-stu-id="d32d6-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="d32d6-105">Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> não está definida, o <xref:System.Windows.Forms.Control.BackColor%2A> seleção preencherá o painel inteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d6-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="d32d6-106">Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> estiver definida, a imagem será exibida por trás de controles contidos.</span><span class="sxs-lookup"><span data-stu-id="d32d6-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="d32d6-107">Definir o plano de fundo de maneira programática</span><span class="sxs-lookup"><span data-stu-id="d32d6-107">To set the background programmatically</span></span>  
  
1.  <span data-ttu-id="d32d6-108">Definir o painel <xref:System.Windows.Forms.Control.BackColor%2A> propriedade para um valor do tipo <xref:System.Drawing.Color?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d32d6-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2.  <span data-ttu-id="d32d6-109">Definir o painel <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade usando o <xref:System.Drawing.Image.FromFile%2A> método o <xref:System.Drawing.Image?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="d32d6-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
    ```vb  
    ' You should replace the bolded image   
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d32d6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d32d6-110">See also</span></span>
- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="d32d6-111">Controle de painel</span><span class="sxs-lookup"><span data-stu-id="d32d6-111">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [<span data-ttu-id="d32d6-112">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="d32d6-112">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
