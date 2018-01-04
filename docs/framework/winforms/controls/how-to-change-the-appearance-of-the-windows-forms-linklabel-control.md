---
title: "Como alterar a aparência do controle LinkLabel dos Windows Forms"
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
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dc3963ab1b242ce8dce53d9bba996f52347679b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Como alterar a aparência do controle LinkLabel dos Windows Forms
Você pode alterar o texto exibido, o <xref:System.Windows.Forms.LinkLabel> controle de acordo com uma variedade de propósitos. Por exemplo, é uma prática comum para indicar ao usuário que o texto é clicável configurando o texto a ser exibido em uma cor específica com um sublinhado. Depois que o usuário clica no texto, a cor é alterada para uma cor diferente. Para controlar esse comportamento, você pode definir propriedades diferentes cinco: o <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, e <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriedades.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Alterar a aparência de um controle LinkLabel  
  
1.  Definir o <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> e <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> propriedades para as cores que você deseja.  
  
     Isso pode ser feito por meio de programação ou no tempo de design na janela **Propriedades**.  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2.  Definir o <xref:System.Windows.Forms.LinkLabel.Text%2A> propriedade como uma legenda apropriada.  
  
     Isso pode ser feito por meio de programação ou no tempo de design na janela **Propriedades**.  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  Definir o <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade para determinar qual parte da legenda será indicado como um link.  
  
     O <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> valor é representado com uma <xref:System.Windows.Forms.LinkArea> que contém dois números, a posição do caractere inicial e o número de caracteres. Isso pode ser feito por meio de programação ou no tempo de design na janela **Propriedades**.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  Definir o <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> propriedade <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, ou <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Se for definido como <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, a parte da legenda determinada pelo <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> será sublinhada somente quando o ponteiro permanece nele.  
  
5.  No <xref:System.Windows.Forms.LinkLabel.LinkClicked> manipulador de eventos, defina o <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriedade `true`.  
  
     Quando um link foi visitado, é uma prática comum alterar sua aparência de alguma maneira, geralmente a cor. O texto será alterado para a cor especificada pelo <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> propriedade.  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>  
 [Visão geral do controle LinkLabel](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [Como vincular a um objeto ou página da Web com o controle LinkLabel dos Windows Forms](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [Controle LinkLabel](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
