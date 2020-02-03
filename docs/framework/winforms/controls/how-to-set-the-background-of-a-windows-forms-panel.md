---
title: Definir a tela de fundo de um painel
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
ms.openlocfilehash: ba2619354403793aea7ca15d43649da9637079a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744737"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="4dc11-102">Como definir a tela de fundo de um painel Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4dc11-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="4dc11-103">Um controle de <xref:System.Windows.Forms.Panel> de Windows Forms pode exibir uma cor de plano de fundo e uma imagem de plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="4dc11-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="4dc11-104">A propriedade <xref:System.Windows.Forms.Control.BackColor%2A> define a cor do plano de fundo dos controles contidos, como rótulos e botões de opção.</span><span class="sxs-lookup"><span data-stu-id="4dc11-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="4dc11-105">Se a propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> não estiver definida, a seleção de <xref:System.Windows.Forms.Control.BackColor%2A> preencherá o painel inteiro.</span><span class="sxs-lookup"><span data-stu-id="4dc11-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="4dc11-106">Se a propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> for definida, a imagem será exibida atrás dos controles contidos.</span><span class="sxs-lookup"><span data-stu-id="4dc11-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="4dc11-107">Para definir o plano de fundo programaticamente</span><span class="sxs-lookup"><span data-stu-id="4dc11-107">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="4dc11-108">Defina a propriedade <xref:System.Windows.Forms.Control.BackColor%2A> do painel como um valor do tipo <xref:System.Drawing.Color?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4dc11-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="4dc11-109">Defina a propriedade de <xref:System.Windows.Forms.Control.BackgroundImage%2A> do painel usando o método <xref:System.Drawing.Image.FromFile%2A> da classe <xref:System.Drawing.Image?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4dc11-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4dc11-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4dc11-110">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="4dc11-111">Controle de painel</span><span class="sxs-lookup"><span data-stu-id="4dc11-111">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="4dc11-112">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="4dc11-112">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
