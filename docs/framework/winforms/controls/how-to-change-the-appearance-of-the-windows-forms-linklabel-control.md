---
title: 'Como: Alterar a aparência do controle LinkLabel do Windows Forms'
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
ms.openlocfilehash: f0a5805561509501ca38a7fec6b4731af190e3c3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322011"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="28d4d-102">Como: Alterar a aparência do controle LinkLabel do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28d4d-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="28d4d-103">Você pode alterar o texto exibido pelo <xref:System.Windows.Forms.LinkLabel> controle para atender a uma variedade de finalidades.</span><span class="sxs-lookup"><span data-stu-id="28d4d-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="28d4d-104">Por exemplo, é uma prática comum para indicar ao usuário que o texto é clicável configurando o texto a ser exibido em uma cor específica com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="28d4d-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="28d4d-105">Depois que o usuário clica no texto, a cor é alterada para uma cor diferente.</span><span class="sxs-lookup"><span data-stu-id="28d4d-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="28d4d-106">Para controlar esse comportamento, você pode definir cinco propriedades diferentes: o <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, e <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="28d4d-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="28d4d-107">Alterar a aparência de um controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="28d4d-107">To change the appearance of a LinkLabel control</span></span>  
  
1. <span data-ttu-id="28d4d-108">Defina as <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> e <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> propriedades para as cores que você deseja.</span><span class="sxs-lookup"><span data-stu-id="28d4d-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="28d4d-109">Isso pode ser feito por meio de programação ou no tempo de design na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="28d4d-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
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
  
2. <span data-ttu-id="28d4d-110">Defina o <xref:System.Windows.Forms.LinkLabel.Text%2A> propriedade para uma legenda apropriada.</span><span class="sxs-lookup"><span data-stu-id="28d4d-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="28d4d-111">Isso pode ser feito por meio de programação ou no tempo de design na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="28d4d-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. <span data-ttu-id="28d4d-112">Defina o <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade para determinar qual parte da legenda será indicada como um link.</span><span class="sxs-lookup"><span data-stu-id="28d4d-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="28d4d-113">O <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> valor é representado com uma <xref:System.Windows.Forms.LinkArea> contendo dois números, a posição do caractere inicial e o número de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28d4d-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="28d4d-114">Isso pode ser feito por meio de programação ou no tempo de design na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="28d4d-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. <span data-ttu-id="28d4d-115">Defina as <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> propriedade para <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, ou <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span><span class="sxs-lookup"><span data-stu-id="28d4d-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="28d4d-116">Se ele for definido como <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, a parte da legenda determinada pelo <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> só será sublinhada quando o ponteiro for posicionado sobre ele.</span><span class="sxs-lookup"><span data-stu-id="28d4d-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5. <span data-ttu-id="28d4d-117">No <xref:System.Windows.Forms.LinkLabel.LinkClicked> manipulador de eventos, defina a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="28d4d-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="28d4d-118">Quando um link foi visitado, é uma prática comum alterar sua aparência de alguma maneira, geralmente a cor.</span><span class="sxs-lookup"><span data-stu-id="28d4d-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="28d4d-119">O texto será alterado para a cor especificada pela <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="28d4d-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28d4d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28d4d-120">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [<span data-ttu-id="28d4d-121">Visão geral do controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="28d4d-121">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="28d4d-122">Como: Vincular a um objeto ou página da Web com o controle LinkLabel do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28d4d-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="28d4d-123">Controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="28d4d-123">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
