---
title: Como adicionar a ou remover de uma coleção de controles em tempo de execução
description: Saiba como adicionar controles e remover controles de qualquer controle de contêiner em seus formulários, como o controle de painel ou GroupBox, ou até mesmo o próprio formulário.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 6c3f2d1f42b130de4d808871265b50510cfb8f47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325858"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="1bf3e-103">Como adicionar a ou remover de uma coleção de controles em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1bf3e-103">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="1bf3e-104">Tarefas comuns no desenvolvimento de aplicativos são adicionar controles e remover controles de qualquer controle de contêiner em seus formulários (como o <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.GroupBox> controle ou, ou até mesmo o próprio formulário).</span><span class="sxs-lookup"><span data-stu-id="1bf3e-104">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="1bf3e-105">Em tempo de design, controles podem ser arrastados diretamente para um painel ou caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-105">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="1bf3e-106">Em tempo de execução, esses controles mantêm uma coleção `Controls`, que mantém o controle de quais controles são colocados neles.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-106">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bf3e-107">O exemplo de código a seguir aplica-se a qualquer controle que mantém uma coleção de controles dentro dele.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-107">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="1bf3e-108">Para adicionar um controle a uma coleção de forma programática</span><span class="sxs-lookup"><span data-stu-id="1bf3e-108">To add a control to a collection programmatically</span></span>  
  
1. <span data-ttu-id="1bf3e-109">Crie uma instância do controle a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-109">Create an instance of the control to be added.</span></span>  
  
2. <span data-ttu-id="1bf3e-110">Defina as propriedades do novo controle.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-110">Set properties of the new control.</span></span>  
  
3. <span data-ttu-id="1bf3e-111">Adicione o controle à coleção `Controls` do controle pai.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-111">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="1bf3e-112">O exemplo de código a seguir mostra como criar uma instância do <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-112">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="1bf3e-113">Ele requer um formulário com um <xref:System.Windows.Forms.Panel> controle e que o método de manipulação de eventos para o botão que está sendo criado, `NewPanelButton_Click` já exista.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-113">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="1bf3e-114">Para remover os controles de uma coleção de forma programática</span><span class="sxs-lookup"><span data-stu-id="1bf3e-114">To remove controls from a collection programmatically</span></span>  
  
1. <span data-ttu-id="1bf3e-115">Remova o manipulador de eventos do evento.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-115">Remove the event handler from the event.</span></span> <span data-ttu-id="1bf3e-116">Em Visual Basic, use a palavra-chave [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) ; em C#, use o [operador-=](../../../csharp/language-reference/operators/subtraction-operator.md).</span><span class="sxs-lookup"><span data-stu-id="1bf3e-116">In Visual Basic, use the [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) keyword; in C#, use the [-= operator](../../../csharp/language-reference/operators/subtraction-operator.md).</span></span>  
  
2. <span data-ttu-id="1bf3e-117">Use o método `Remove` para excluir o controle desejado da coleção `Controls` do painel.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-117">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3. <span data-ttu-id="1bf3e-118">Chame o <xref:System.Windows.Forms.Control.Dispose%2A> método para liberar todos os recursos usados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="1bf3e-118">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1bf3e-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="1bf3e-119">See also</span></span>

- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="1bf3e-120">Controle de painel</span><span class="sxs-lookup"><span data-stu-id="1bf3e-120">Panel Control</span></span>](panel-control-windows-forms.md)
