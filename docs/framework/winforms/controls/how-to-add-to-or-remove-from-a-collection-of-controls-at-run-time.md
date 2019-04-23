---
title: 'Como: Adicionar a ou remover de uma coleção de controles em tempo de execução'
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
ms.openlocfilehash: 85c1d398c1aabbb73d5ae34186775e2c63666cfb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59309440"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="3b10e-102">Como: Adicionar a ou remover de uma coleção de controles em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3b10e-102">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="3b10e-103">Tarefas comuns no desenvolvimento de aplicativos são adicionar controles para e remover controles de qualquer controle de contêiner em formulários (como o <xref:System.Windows.Forms.Panel> ou <xref:System.Windows.Forms.GroupBox> controle ou até mesmo o próprio formulário).</span><span class="sxs-lookup"><span data-stu-id="3b10e-103">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="3b10e-104">Em tempo de design, controles podem ser arrastados diretamente para um painel ou caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="3b10e-104">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="3b10e-105">Em tempo de execução, esses controles mantêm uma coleção `Controls`, que mantém o controle de quais controles são colocados neles.</span><span class="sxs-lookup"><span data-stu-id="3b10e-105">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b10e-106">O exemplo de código a seguir aplica-se a qualquer controle que mantém uma coleção de controles dentro dele.</span><span class="sxs-lookup"><span data-stu-id="3b10e-106">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="3b10e-107">Para adicionar um controle a uma coleção de forma programática</span><span class="sxs-lookup"><span data-stu-id="3b10e-107">To add a control to a collection programmatically</span></span>  
  
1. <span data-ttu-id="3b10e-108">Crie uma instância do controle a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="3b10e-108">Create an instance of the control to be added.</span></span>  
  
2. <span data-ttu-id="3b10e-109">Defina as propriedades do novo controle.</span><span class="sxs-lookup"><span data-stu-id="3b10e-109">Set properties of the new control.</span></span>  
  
3. <span data-ttu-id="3b10e-110">Adicione o controle à coleção `Controls` do controle pai.</span><span class="sxs-lookup"><span data-stu-id="3b10e-110">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="3b10e-111">O exemplo de código a seguir mostra como criar uma instância da <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="3b10e-111">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="3b10e-112">Ele exige um formulário com um <xref:System.Windows.Forms.Panel> controle e que o método de manipulação de eventos para o botão que está sendo criado, `NewPanelButton_Click`, já existe.</span><span class="sxs-lookup"><span data-stu-id="3b10e-112">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="3b10e-113">Para remover os controles de uma coleção de forma programática</span><span class="sxs-lookup"><span data-stu-id="3b10e-113">To remove controls from a collection programmatically</span></span>  
  
1. <span data-ttu-id="3b10e-114">Remova o manipulador de eventos do evento.</span><span class="sxs-lookup"><span data-stu-id="3b10e-114">Remove the event handler from the event.</span></span> <span data-ttu-id="3b10e-115">No Visual Basic, use o [Instrução RemoveHandler](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) palavra-chave; no Visual C#, use o [-= operador (C# referência)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3b10e-115">In Visual Basic, use the [RemoveHandler Statement](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) keyword; in Visual C#, use the [-= Operator (C# Reference)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).</span></span>  
  
2. <span data-ttu-id="3b10e-116">Use o método `Remove` para excluir o controle desejado da coleção `Controls` do painel.</span><span class="sxs-lookup"><span data-stu-id="3b10e-116">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3. <span data-ttu-id="3b10e-117">Chamar o <xref:System.Windows.Forms.Control.Dispose%2A> método para liberar todos os recursos usados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="3b10e-117">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b10e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b10e-118">See also</span></span>

- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="3b10e-119">Controle de painel</span><span class="sxs-lookup"><span data-stu-id="3b10e-119">Panel Control</span></span>](panel-control-windows-forms.md)
