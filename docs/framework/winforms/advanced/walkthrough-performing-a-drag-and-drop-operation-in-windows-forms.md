---
title: "Instruções passo a passo: executando uma operação de arrastar e soltar no Windows Forms"
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
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173af57f1ec5d9ed14afc0ef5d6ddd391e15d534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="f48ef-102">Instruções passo a passo: executando uma operação de arrastar e soltar no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f48ef-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="f48ef-103">Para executar operações de arrastar e soltar em aplicativos baseados no Windows você precisa lidar uma série de eventos, particularmente o <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, e <xref:System.Windows.Forms.Control.DragDrop> eventos.</span><span class="sxs-lookup"><span data-stu-id="f48ef-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="f48ef-104">Trabalhando com as informações disponíveis no evento argumentos desses eventos, você pode facilmente orientar as operações do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="f48ef-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="f48ef-105">Arrastando dados</span><span class="sxs-lookup"><span data-stu-id="f48ef-105">Dragging Data</span></span>  
 <span data-ttu-id="f48ef-106">Todas as operações do tipo "arrastar e soltar" começam com arrastar.</span><span class="sxs-lookup"><span data-stu-id="f48ef-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="f48ef-107">A funcionalidade de permitir que dados sejam coletados quando o arrastamento começa é implementada no <xref:System.Windows.Forms.Control.DoDragDrop%2A> método.</span><span class="sxs-lookup"><span data-stu-id="f48ef-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="f48ef-108">No exemplo a seguir, o <xref:System.Windows.Forms.Control.MouseDown> eventos é usado para iniciar a operação de arrastar porque ele é o mais intuitivo (a maioria das ações de arrastar e soltar começa com o botão do mouse sendo pressionado).</span><span class="sxs-lookup"><span data-stu-id="f48ef-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="f48ef-109">No entanto, lembre-se de que qualquer evento pode ser usado para iniciar um procedimento do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="f48ef-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f48ef-110">Determinados controles têm eventos específicos de arrastar personalizados.</span><span class="sxs-lookup"><span data-stu-id="f48ef-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="f48ef-111">O <xref:System.Windows.Forms.ListView> e <xref:System.Windows.Forms.TreeView> controles, por exemplo, tem um <xref:System.Windows.Forms.TreeView.ItemDrag> eventos.</span><span class="sxs-lookup"><span data-stu-id="f48ef-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="f48ef-112">Para iniciar uma operação de arrastar</span><span class="sxs-lookup"><span data-stu-id="f48ef-112">To start a drag operation</span></span>  
  
1.  <span data-ttu-id="f48ef-113">No <xref:System.Windows.Forms.Control.MouseDown> eventos para o controle onde o arrastamento começará, use o `DoDragDrop` terão método para definir os dados a serem arrastados e o efeito permitido.</span><span class="sxs-lookup"><span data-stu-id="f48ef-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="f48ef-114">Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Data%2A> e <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="f48ef-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="f48ef-115">O exemplo a seguir mostra como iniciar uma operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="f48ef-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="f48ef-116">O controle onde começa a arrastar um <xref:System.Windows.Forms.Button> controle, os dados que está sendo arrastados é a cadeia de caracteres que representa o <xref:System.Windows.Forms.Control.Text%2A> propriedade o <xref:System.Windows.Forms.Button> controle e os efeitos permitidos são copiar ou mover.</span><span class="sxs-lookup"><span data-stu-id="f48ef-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f48ef-117">Nenhum dado pode ser usado como um parâmetro no `DoDragDrop` método; no exemplo acima, o <xref:System.Windows.Forms.Control.Text%2A> propriedade o <xref:System.Windows.Forms.Button> controle foi usado (em vez de embutir um valor ou recuperar dados de um conjunto de dados) porque a propriedade estava relacionada com o local que está sendo arrastada (o <xref:System.Windows.Forms.Button> controle).</span><span class="sxs-lookup"><span data-stu-id="f48ef-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="f48ef-118">Lembre-se disso ao incorporar operações do tipo "arrastar e soltar" em seus aplicativos baseados em Windows.</span><span class="sxs-lookup"><span data-stu-id="f48ef-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="f48ef-119">Enquanto uma operação de arrastar estiver em vigor, você pode manipular o <xref:System.Windows.Forms.Control.QueryContinueDrag> evento, que "pede a permissão" do sistema para continuar a operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="f48ef-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="f48ef-120">Ao lidar com esse método, também é o ponto apropriado para você chamar métodos que terão um efeito sobre a operação de arrastar, como expandir um <xref:System.Windows.Forms.TreeNode> em um <xref:System.Windows.Forms.TreeView> controlar quando o cursor passa sobre ele.</span><span class="sxs-lookup"><span data-stu-id="f48ef-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="f48ef-121">Descartando dados</span><span class="sxs-lookup"><span data-stu-id="f48ef-121">Dropping Data</span></span>  
 <span data-ttu-id="f48ef-122">Depois de começar a arrastar dados de um local em um Formulário ou controle do Windows, você naturalmente desejará soltá-los em algum lugar.</span><span class="sxs-lookup"><span data-stu-id="f48ef-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="f48ef-123">O cursor mudará ao cruzar uma área de um formulário ou controle que esteja configurado corretamente para receber os dados soltados.</span><span class="sxs-lookup"><span data-stu-id="f48ef-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="f48ef-124">Qualquer área em um formulário do Windows ou controle pode ser feita para aceitar dados soltos, definindo a <xref:System.Windows.Forms.Control.AllowDrop%2A> propriedade e tratamento de <xref:System.Windows.Forms.Control.DragEnter> e <xref:System.Windows.Forms.Control.DragDrop> eventos.</span><span class="sxs-lookup"><span data-stu-id="f48ef-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="f48ef-125">Para executar uma operação de soltar</span><span class="sxs-lookup"><span data-stu-id="f48ef-125">To perform a drop</span></span>  
  
1.  <span data-ttu-id="f48ef-126">Definir o <xref:System.Windows.Forms.Control.AllowDrop%2A> propriedade como true.</span><span class="sxs-lookup"><span data-stu-id="f48ef-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2.  <span data-ttu-id="f48ef-127">No `DragEnter` eventos para o controle onde o descarte ocorrerá, certifique-se de que os dados que está sendo arrastados são de um tipo aceitável (neste caso, <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="f48ef-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="f48ef-128">O código define o efeito que acontecerá quando o descarte ocorre para um valor na <xref:System.Windows.Forms.DragDropEffects> enumeração.</span><span class="sxs-lookup"><span data-stu-id="f48ef-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="f48ef-129">Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="f48ef-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f48ef-130">Você pode definir suas próprias <xref:System.Windows.Forms.DataFormats> especificando seu próprio objeto como o <xref:System.Object> parâmetro o <xref:System.Windows.Forms.DataObject.SetData%2A> método.</span><span class="sxs-lookup"><span data-stu-id="f48ef-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="f48ef-131">Ao fazer isso, verifique se o objeto especificado é serializável.</span><span class="sxs-lookup"><span data-stu-id="f48ef-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="f48ef-132">Para obter mais informações, consulte <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="f48ef-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3.  <span data-ttu-id="f48ef-133">No <xref:System.Windows.Forms.Control.DragDrop> eventos para o controle onde a operação de soltar irá ocorrer, use o <xref:System.Windows.Forms.DataObject.GetData%2A> método para recuperar os dados que está sendo arrastados.</span><span class="sxs-lookup"><span data-stu-id="f48ef-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="f48ef-134">Para obter mais informações, consulte <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="f48ef-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="f48ef-135">No exemplo a seguir, um <xref:System.Windows.Forms.TextBox> controle é o controle sendo arrastado para (onde a operação de soltar irá ocorrer).</span><span class="sxs-lookup"><span data-stu-id="f48ef-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="f48ef-136">O código define o <xref:System.Windows.Forms.Control.Text%2A> propriedade o <xref:System.Windows.Forms.TextBox> controlar igual aos dados que está sendo arrastados.</span><span class="sxs-lookup"><span data-stu-id="f48ef-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f48ef-137">Além disso, você pode trabalhar com o <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> propriedade, para que, dependendo das teclas pressionadas durante a operação de arrastar e soltar, determinados efeitos ocorram (por exemplo, ele é padrão para copiar os dados arrastados quando a tecla CTRL pressionada).</span><span class="sxs-lookup"><span data-stu-id="f48ef-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48ef-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f48ef-138">See Also</span></span>  
 [<span data-ttu-id="f48ef-139">Como Adicionar Dados à Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="f48ef-139">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [<span data-ttu-id="f48ef-140">Como Recuperar Dados da Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="f48ef-140">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [<span data-ttu-id="f48ef-141">Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="f48ef-141">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
