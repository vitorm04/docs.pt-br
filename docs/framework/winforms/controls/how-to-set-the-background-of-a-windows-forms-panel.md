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
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Como definir a tela de fundo de um painel Windows Forms
Um controle de <xref:System.Windows.Forms.Panel> de Windows Forms pode exibir uma cor de plano de fundo e uma imagem de plano de fundo. A propriedade <xref:System.Windows.Forms.Control.BackColor%2A> define a cor do plano de fundo dos controles contidos, como rótulos e botões de opção. Se a propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> não estiver definida, a seleção de <xref:System.Windows.Forms.Control.BackColor%2A> preencherá o painel inteiro. Se a propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> for definida, a imagem será exibida atrás dos controles contidos.  
  
### <a name="to-set-the-background-programmatically"></a>Para definir o plano de fundo programaticamente  
  
1. Defina a propriedade <xref:System.Windows.Forms.Control.BackColor%2A> do painel como um valor do tipo <xref:System.Drawing.Color?displayProperty=nameWithType>.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Defina a propriedade de <xref:System.Windows.Forms.Control.BackgroundImage%2A> do painel usando o método <xref:System.Drawing.Image.FromFile%2A> da classe <xref:System.Drawing.Image?displayProperty=nameWithType>.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Controle de painel](panel-control-windows-forms.md)
- [Visão geral do controle Panel](panel-control-overview-windows-forms.md)
