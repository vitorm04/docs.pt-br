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
ms.openlocfilehash: 36e552475334c25b9d5a6fafb82155c6ebcba266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182102"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Como definir a tela de fundo de um painel Windows Forms
Um controle <xref:System.Windows.Forms.Panel> do Windows Forms pode exibir uma cor de fundo e uma imagem de fundo. A <xref:System.Windows.Forms.Control.BackColor%2A> propriedade define a cor de fundo para os controles contidos, como etiquetas e botões de rádio. Se <xref:System.Windows.Forms.Control.BackgroundImage%2A> a propriedade não <xref:System.Windows.Forms.Control.BackColor%2A> estiver definida, a seleção preencherá todo o painel. Se <xref:System.Windows.Forms.Control.BackgroundImage%2A> a propriedade estiver definida, a imagem será exibida atrás dos controles contidos.  
  
### <a name="to-set-the-background-programmatically"></a>Para definir o plano de fundo programáticamente  
  
1. Defina a <xref:System.Windows.Forms.Control.BackColor%2A> propriedade do painel <xref:System.Drawing.Color?displayProperty=nameWithType>como um valor de tipo .  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Defina a <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade do <xref:System.Drawing.Image.FromFile%2A> painel <xref:System.Drawing.Image?displayProperty=nameWithType> usando o método da classe.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Controle de painel](panel-control-windows-forms.md)
- [Visão geral do controle Panel](panel-control-overview-windows-forms.md)
