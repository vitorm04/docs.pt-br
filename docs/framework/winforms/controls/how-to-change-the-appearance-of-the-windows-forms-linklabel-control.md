---
title: Alterar a aparência do controle linklabel
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
ms.openlocfilehash: df66991289373a05fc7c27b7768a96643e3bbae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142124"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Como alterar a aparência do controle LinkLabel dos Windows Forms
Você pode alterar o texto <xref:System.Windows.Forms.LinkLabel> exibido pelo controle para se adequar a uma variedade de propósitos. Por exemplo, é uma prática comum para indicar ao usuário que o texto é clicável configurando o texto a ser exibido em uma cor específica com um sublinhado. Depois que o usuário clica no texto, a cor é alterada para uma cor diferente. Para controlar esse comportamento, você pode <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>definir <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>cinco <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>propriedades <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> diferentes: as propriedades, e propriedades.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Alterar a aparência de um controle LinkLabel  
  
1. Defina <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> as propriedades e as propriedades para as cores desejadas.  
  
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
  
2. Defina <xref:System.Windows.Forms.LinkLabel.Text%2A> a propriedade como uma legenda apropriada.  
  
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
  
3. Defina <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> a propriedade para determinar qual parte da legenda será indicada como um link.  
  
     O <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> valor é <xref:System.Windows.Forms.LinkArea> representado com dois números contendo, a posição de caractere inicial e o número de caracteres. Isso pode ser feito por meio de programação ou no tempo de design na janela **Propriedades**.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. Defina <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> a <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline> <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>propriedade <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>como, ou .  
  
     Se for definido <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>como , a parte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> da legenda determinada por só será sublinhada quando o ponteiro repousa sobre ele.  
  
5. No <xref:System.Windows.Forms.LinkLabel.LinkClicked> manipulador de eventos, defina a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriedade como `true`.  
  
     Quando um link foi visitado, é uma prática comum alterar sua aparência de alguma maneira, geralmente a cor. O texto mudará para a cor <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> especificada pela propriedade.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [Visão geral do controle LinkLabel](linklabel-control-overview-windows-forms.md)
- [Como vincular a um objeto ou página da Web com o controle LinkLabel dos Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Controle LinkLabel](linklabel-control-windows-forms.md)
