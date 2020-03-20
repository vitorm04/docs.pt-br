---
title: Como acionar eventos de menu para botões da barra de ferramentas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
ms.openlocfilehash: 99db077b41a59fe9263f7283b58b8c31959c7c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182073"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="a71bd-102">Como acionar eventos de menu para botões da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a71bd-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
> <span data-ttu-id="a71bd-103">O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="a71bd-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="a71bd-104">Se o formulário <xref:System.Windows.Forms.ToolBar> do Windows possui um controle com botões de barra de ferramentas, você vai querer saber em qual botão o usuário clica.</span><span class="sxs-lookup"><span data-stu-id="a71bd-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="a71bd-105">No <xref:System.Windows.Forms.ToolBar.ButtonClick> caso do <xref:System.Windows.Forms.ToolBar> controle, você <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> pode avaliar <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> a propriedade da classe.</span><span class="sxs-lookup"><span data-stu-id="a71bd-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="a71bd-106">No exemplo a seguir, uma caixa de mensagem é exibida, indicando qual botão foi clicado.</span><span class="sxs-lookup"><span data-stu-id="a71bd-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="a71bd-107">Para obter detalhes, consulte <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="a71bd-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="a71bd-108">O exemplo abaixo <xref:System.Windows.Forms.ToolBar> assume que um controle foi adicionado a um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="a71bd-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="a71bd-109">Para manipular o evento de Clique na barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a71bd-109">To handle the Click event on a toolbar</span></span>  
  
1. <span data-ttu-id="a71bd-110">Em um procedimento, adicione botões <xref:System.Windows.Forms.ToolBar> de barra de ferramentas ao controle.</span><span class="sxs-lookup"><span data-stu-id="a71bd-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
    ```  
  
    ```csharp  
    public void ToolBarConfig()
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2. <span data-ttu-id="a71bd-111">Adicione um manipulador <xref:System.Windows.Forms.ToolBar> de eventos <xref:System.Windows.Forms.ToolBar.ButtonClick> para o evento do controle.</span><span class="sxs-lookup"><span data-stu-id="a71bd-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="a71bd-112">Use uma declaração de <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> comutação de caso e a classe para determinar o botão da barra de ferramentas que foi clicado.</span><span class="sxs-lookup"><span data-stu-id="a71bd-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="a71bd-113">Com base nisso, exiba a caixa de mensagem apropriada.</span><span class="sxs-lookup"><span data-stu-id="a71bd-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a71bd-114">Uma caixa de mensagem está sendo usada apenas como um espaço reservado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="a71bd-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="a71bd-115">Fique à vontade para adicionar outro código para ser executado quando os botões da barra de ferramentas forem clicados.</span><span class="sxs-lookup"><span data-stu-id="a71bd-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a71bd-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a71bd-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="a71bd-117">Como adicionar botões a um controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a71bd-117">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)
- [<span data-ttu-id="a71bd-118">Como definir um ícone para um botão de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a71bd-118">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="a71bd-119">Controle ToolBar</span><span class="sxs-lookup"><span data-stu-id="a71bd-119">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
