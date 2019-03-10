---
title: 'Como: Disparar eventos de Menu para botões da barra de ferramentas'
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
ms.openlocfilehash: b6d0404f22c7db72b096ef130d9a9f4815db4059
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707541"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="80e0f-102">Como: Disparar eventos de Menu para botões da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="80e0f-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
>  <span data-ttu-id="80e0f-103">O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="80e0f-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="80e0f-104">Se seus recursos de formulário do Windows uma <xref:System.Windows.Forms.ToolBar> controle com os botões da barra de ferramentas, você desejará saber qual botão o usuário clica.</span><span class="sxs-lookup"><span data-stu-id="80e0f-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="80e0f-105">No <xref:System.Windows.Forms.ToolBar.ButtonClick> eventos do <xref:System.Windows.Forms.ToolBar> controle, você pode avaliar o <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> propriedade do <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> classe.</span><span class="sxs-lookup"><span data-stu-id="80e0f-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="80e0f-106">No exemplo a seguir, uma caixa de mensagem é exibida, indicando qual botão foi clicado.</span><span class="sxs-lookup"><span data-stu-id="80e0f-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="80e0f-107">Para obter detalhes, consulte <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="80e0f-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="80e0f-108">O exemplo a seguir supõe um <xref:System.Windows.Forms.ToolBar> controle foi adicionado a um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="80e0f-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="80e0f-109">Para manipular o evento de Clique na barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="80e0f-109">To handle the Click event on a toolbar</span></span>  
  
1.  <span data-ttu-id="80e0f-110">Em um procedimento, adicione botões de barra de ferramentas para o <xref:System.Windows.Forms.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="80e0f-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
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
  
2.  <span data-ttu-id="80e0f-111">Adicionar um manipulador de eventos para o <xref:System.Windows.Forms.ToolBar> do controle <xref:System.Windows.Forms.ToolBar.ButtonClick> eventos.</span><span class="sxs-lookup"><span data-stu-id="80e0f-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="80e0f-112">Um instrução de comutação de caso de uso e o <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> classe para determinar o botão de barra de ferramentas que foi clicado.</span><span class="sxs-lookup"><span data-stu-id="80e0f-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="80e0f-113">Com base nisso, exiba a caixa de mensagem apropriada.</span><span class="sxs-lookup"><span data-stu-id="80e0f-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="80e0f-114">Uma caixa de mensagem está sendo usada apenas como um espaço reservado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="80e0f-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="80e0f-115">Fique à vontade para adicionar outro código para ser executado quando os botões da barra de ferramentas forem clicados.</span><span class="sxs-lookup"><span data-stu-id="80e0f-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="80e0f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80e0f-116">See also</span></span>
- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="80e0f-117">Como: Adicionar botões a um controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="80e0f-117">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)
- [<span data-ttu-id="80e0f-118">Como: Definir um ícone para um botão de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="80e0f-118">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="80e0f-119">Controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="80e0f-119">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
