---
title: 'Passo a passo: executar uma operação do tipo "arrastar e soltar" no Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: cda3e87a4b0eb680d374eb0419a6b6b3157dc4a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957129"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="c774b-102">Passo a passo: executar uma operação do tipo "arrastar e soltar" no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c774b-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="c774b-103">Para executar operações de arrastar e soltar em aplicativos baseados no Windows, você deve lidar com uma série de eventos, principalmente os <xref:System.Windows.Forms.Control.DragEnter>eventos <xref:System.Windows.Forms.Control.DragLeave>, e <xref:System.Windows.Forms.Control.DragDrop> .</span><span class="sxs-lookup"><span data-stu-id="c774b-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="c774b-104">Trabalhando com as informações disponíveis no evento argumentos desses eventos, você pode facilmente orientar as operações do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="c774b-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="c774b-105">Arrastando dados</span><span class="sxs-lookup"><span data-stu-id="c774b-105">Dragging Data</span></span>  
 <span data-ttu-id="c774b-106">Todas as operações do tipo "arrastar e soltar" começam com arrastar.</span><span class="sxs-lookup"><span data-stu-id="c774b-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="c774b-107">A funcionalidade para habilitar os dados a serem coletados ao arrastar iniciar é implementada no <xref:System.Windows.Forms.Control.DoDragDrop%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c774b-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="c774b-108">No exemplo a seguir, o <xref:System.Windows.Forms.Control.MouseDown> evento é usado para iniciar a operação de arrastar porque ela é a mais intuitiva (a maioria das ações de arrastar e soltar começa com o botão do mouse que está sendo pressionado).</span><span class="sxs-lookup"><span data-stu-id="c774b-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="c774b-109">No entanto, lembre-se de que qualquer evento pode ser usado para iniciar um procedimento do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="c774b-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c774b-110">Determinados controles têm eventos específicos de arrastar personalizados.</span><span class="sxs-lookup"><span data-stu-id="c774b-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="c774b-111">Os <xref:System.Windows.Forms.ListView> controles <xref:System.Windows.Forms.TreeView> e, por exemplo, têm um <xref:System.Windows.Forms.TreeView.ItemDrag> evento.</span><span class="sxs-lookup"><span data-stu-id="c774b-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="c774b-112">Para iniciar uma operação de arrastar</span><span class="sxs-lookup"><span data-stu-id="c774b-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="c774b-113">No evento para o controle em que o arrastar será iniciado, use o `DoDragDrop` método para definir os dados a serem arrastados e o efeito permitido ao arrastar terá. <xref:System.Windows.Forms.Control.MouseDown></span><span class="sxs-lookup"><span data-stu-id="c774b-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="c774b-114">Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Data%2A> e <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="c774b-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="c774b-115">O exemplo a seguir mostra como iniciar uma operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="c774b-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="c774b-116">O controle em que o arrastar começa é <xref:System.Windows.Forms.Button> um controle, os dados que estão sendo arrastados são <xref:System.Windows.Forms.Control.Text%2A> a cadeia de <xref:System.Windows.Forms.Button> caracteres que representa a propriedade do controle e os efeitos permitidos estão sendo copiados ou movidos.</span><span class="sxs-lookup"><span data-stu-id="c774b-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="c774b-117">Todos os dados podem ser usados como um parâmetro no `DoDragDrop` método; no exemplo acima, a <xref:System.Windows.Forms.Control.Text%2A> Propriedade do <xref:System.Windows.Forms.Button> controle foi usada (em vez de embutir em código um valor ou recuperar dados de um DataSet) porque a propriedade estava relacionada ao local que está sendo arrastado <xref:System.Windows.Forms.Button> (o controle).</span><span class="sxs-lookup"><span data-stu-id="c774b-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="c774b-118">Lembre-se disso ao incorporar operações do tipo "arrastar e soltar" em seus aplicativos baseados em Windows.</span><span class="sxs-lookup"><span data-stu-id="c774b-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="c774b-119">Embora uma operação de arrastar esteja em vigor, você pode manipular <xref:System.Windows.Forms.Control.QueryContinueDrag> o evento, que "pede permissão" do sistema para continuar a operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="c774b-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="c774b-120">Ao lidar com esse método, também é o ponto apropriado para você chamar métodos que terão um efeito na operação de arrastar, como expandir um <xref:System.Windows.Forms.TreeNode> em um <xref:System.Windows.Forms.TreeView> controle quando o cursor passar sobre ele.</span><span class="sxs-lookup"><span data-stu-id="c774b-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="c774b-121">Descartando dados</span><span class="sxs-lookup"><span data-stu-id="c774b-121">Dropping Data</span></span>  
 <span data-ttu-id="c774b-122">Depois de começar a arrastar dados de um local em um Formulário ou controle do Windows, você naturalmente desejará soltá-los em algum lugar.</span><span class="sxs-lookup"><span data-stu-id="c774b-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="c774b-123">O cursor mudará ao cruzar uma área de um formulário ou controle que esteja configurado corretamente para receber os dados soltados.</span><span class="sxs-lookup"><span data-stu-id="c774b-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="c774b-124">Qualquer área dentro de um formulário ou controle do Windows pode ser feita para aceitar dados eliminados <xref:System.Windows.Forms.Control.AllowDrop%2A> definindo a propriedade e <xref:System.Windows.Forms.Control.DragEnter> manipulando os eventos e <xref:System.Windows.Forms.Control.DragDrop> .</span><span class="sxs-lookup"><span data-stu-id="c774b-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="c774b-125">Para executar uma operação de soltar</span><span class="sxs-lookup"><span data-stu-id="c774b-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="c774b-126">Defina a <xref:System.Windows.Forms.Control.AllowDrop%2A> Propriedade como true.</span><span class="sxs-lookup"><span data-stu-id="c774b-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="c774b-127">No caso do controle onde o descarte ocorrerá, verifique se os dados que estão sendo arrastados são de um tipo aceitável (nesse caso, <xref:System.Windows.Forms.Control.Text%2A>). `DragEnter`</span><span class="sxs-lookup"><span data-stu-id="c774b-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="c774b-128">Em seguida, o código define o efeito que ocorrerá quando a ação de soltar ocorrer em <xref:System.Windows.Forms.DragDropEffects> um valor na enumeração.</span><span class="sxs-lookup"><span data-stu-id="c774b-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="c774b-129">Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="c774b-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="c774b-130">Você pode definir seu próprio <xref:System.Windows.Forms.DataFormats> especificando seu próprio objeto como o <xref:System.Object> parâmetro do <xref:System.Windows.Forms.DataObject.SetData%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c774b-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="c774b-131">Ao fazer isso, verifique se o objeto especificado é serializável.</span><span class="sxs-lookup"><span data-stu-id="c774b-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="c774b-132">Para obter mais informações, consulte <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="c774b-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="c774b-133">No caso do controle em que o drop ocorrerá, use o <xref:System.Windows.Forms.DataObject.GetData%2A> método para recuperar os dados que estão sendo arrastados. <xref:System.Windows.Forms.Control.DragDrop></span><span class="sxs-lookup"><span data-stu-id="c774b-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="c774b-134">Para obter mais informações, consulte <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="c774b-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="c774b-135">No exemplo a seguir, um <xref:System.Windows.Forms.TextBox> controle é o controle que está sendo arrastado para (onde o descarte ocorrerá).</span><span class="sxs-lookup"><span data-stu-id="c774b-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="c774b-136">O código define a <xref:System.Windows.Forms.Control.Text%2A> propriedade <xref:System.Windows.Forms.TextBox> do controle igual aos dados que estão sendo arrastados.</span><span class="sxs-lookup"><span data-stu-id="c774b-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="c774b-137">Além disso, você pode trabalhar com <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> a propriedade, de modo que, dependendo das chaves pressionadas durante a operação de arrastar e soltar, certos efeitos ocorram (por exemplo, é padrão para copiar os dados arrastados quando a tecla CTRL é pressionada).</span><span class="sxs-lookup"><span data-stu-id="c774b-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c774b-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c774b-138">See also</span></span>

- [<span data-ttu-id="c774b-139">Como: Adicionar dados à área de transferência</span><span class="sxs-lookup"><span data-stu-id="c774b-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="c774b-140">Como: Recuperar dados da área de transferência</span><span class="sxs-lookup"><span data-stu-id="c774b-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="c774b-141">Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="c774b-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
