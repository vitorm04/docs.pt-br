---
title: 'Como: Alterar a aparência do controle LinkLabel dos Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: 451faf04e3a51e7dbcb992feb3f38025894be631
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717720"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Como: Alterar a aparência do controle LinkLabel dos Windows Forms
Você pode alterar o texto exibido pelo <xref:System.Windows.Forms.LinkLabel> controle para atender a uma variedade de finalidades. Por exemplo, é uma prática comum para indicar ao usuário que o texto é clicável configurando o texto a ser exibido em uma cor específica com um sublinhado. Depois que o usuário clica no texto, a cor é alterada para uma cor diferente. Para controlar esse comportamento, você pode definir cinco propriedades diferentes: o <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, e <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriedades.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Alterar a aparência de um controle LinkLabel  
  
1.  Defina as <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> e <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> propriedades para as cores que você deseja.  
  
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
  
2.  Defina o <xref:System.Windows.Forms.LinkLabel.Text%2A> propriedade para uma legenda apropriada.  
  
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
  
3.  Defina o <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade para determinar qual parte da legenda será indicada como um link.  
  
     O <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> valor é representado com uma <xref:System.Windows.Forms.LinkArea> contendo dois números, a posição do caractere inicial e o número de caracteres. Isso pode ser feito por meio de programação ou no tempo de design na janela **Propriedades**.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  Defina as <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> propriedade para <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, ou <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Se ele for definido como <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, a parte da legenda determinada pelo <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> só será sublinhada quando o ponteiro for posicionado sobre ele.  
  
5.  No <xref:System.Windows.Forms.LinkLabel.LinkClicked> manipulador de eventos, defina a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriedade `true`.  
  
     Quando um link foi visitado, é uma prática comum alterar sua aparência de alguma maneira, geralmente a cor. O texto será alterado para a cor especificada pela <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> propriedade.  
  
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
- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [Visão geral do controle LinkLabel](linklabel-control-overview-windows-forms.md)
- [Como: Vincular a um objeto ou página com o controle LinkLabel dos Windows Forms da Web](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Controle LinkLabel](linklabel-control-windows-forms.md)
