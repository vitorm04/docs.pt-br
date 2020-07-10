---
title: Definir a tela de fundo de um painel
description: Saiba como definir a cor do plano de fundo e a imagem de plano de fundo de um painel de Windows Forms usando o designer.
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
ms.openlocfilehash: 109ff6184de9c79d1576207bbeb29ad939670b6f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173374"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="37f28-103">Como definir a tela de fundo de um painel Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37f28-103">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="37f28-104">Um controle de Windows Forms <xref:System.Windows.Forms.Panel> pode exibir uma cor de plano de fundo e uma imagem de tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="37f28-104">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="37f28-105">A <xref:System.Windows.Forms.Control.BackColor%2A> propriedade define a cor do plano de fundo para os controles contidos, como rótulos e botões de opção.</span><span class="sxs-lookup"><span data-stu-id="37f28-105">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="37f28-106">Se a <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade não for definida, a <xref:System.Windows.Forms.Control.BackColor%2A> seleção preencherá o painel inteiro.</span><span class="sxs-lookup"><span data-stu-id="37f28-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="37f28-107">Se a <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade for definida, a imagem será exibida atrás dos controles contidos.</span><span class="sxs-lookup"><span data-stu-id="37f28-107">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="37f28-108">Para definir o plano de fundo programaticamente</span><span class="sxs-lookup"><span data-stu-id="37f28-108">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="37f28-109">Defina a propriedade do painel <xref:System.Windows.Forms.Control.BackColor%2A> como um valor do tipo <xref:System.Drawing.Color?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="37f28-109">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="37f28-110">Defina a propriedade do painel <xref:System.Windows.Forms.Control.BackgroundImage%2A> usando o <xref:System.Drawing.Image.FromFile%2A> método da <xref:System.Drawing.Image?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="37f28-110">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37f28-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="37f28-111">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="37f28-112">Controle de painel</span><span class="sxs-lookup"><span data-stu-id="37f28-112">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="37f28-113">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="37f28-113">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
