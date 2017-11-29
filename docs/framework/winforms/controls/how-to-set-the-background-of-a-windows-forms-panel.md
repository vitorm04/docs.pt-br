---
title: Como definir a tela de fundo de um painel Windows Forms
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
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60a1c89375ac7ce9bdefaa051b51ac50be861903
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Como definir a tela de fundo de um painel Windows Forms
Um Windows Forms <xref:System.Windows.Forms.Panel> controle pode exibir uma cor de plano de fundo e uma imagem de plano de fundo. O <xref:System.Windows.Forms.Control.BackColor%2A> propriedade define a cor de plano de fundo de controles contidos, como os rótulos e botões de opção. Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade não for definida, o <xref:System.Windows.Forms.Control.BackColor%2A> seleção preencherá o painel inteiro. Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> estiver definida, a imagem será exibida atrás de controles contidos.  
  
### <a name="to-set-the-background-programmatically"></a>Para definir o plano de fundo programaticamente  
  
1.  Definir o painel <xref:System.Windows.Forms.Control.BackColor%2A> propriedade para um valor do tipo <xref:System.Drawing.Color?displayProperty=nameWithType>.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2.  Definir o painel <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade usando o <xref:System.Drawing.Image.FromFile%2A> método o <xref:System.Drawing.Image?displayProperty=nameWithType> classe.  
  
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
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [Controle de painel](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Visão geral do controle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
