---
title: 'Como: Controlar o ponto de inserção em um controle TextBox do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: 1fa6e8a3642086f81d0a62502d801ec6ade9b3d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110710"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="f7c5b-102">Como: Controlar o ponto de inserção em um controle TextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7c5b-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="f7c5b-103">Quando um Windows Forms <xref:System.Windows.Forms.TextBox> controle primeiro recebe o foco, a inserção padrão na caixa de texto está à esquerda do texto existente.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="f7c5b-104">O usuário pode mover o ponto de inserção com o teclado ou o mouse.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="f7c5b-105">Se a caixa de texto perder e recuperar o foco, o ponto de inserção será sempre o ponto em que o usuário o colocou por último.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="f7c5b-106">Em alguns casos, esse comportamento pode ser desconcertante para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="f7c5b-107">Em um aplicativo de processamento de texto, o usuário pode esperar que novos caracteres apareçam após o texto existente.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="f7c5b-108">Em um aplicativo de entrada de dados, o usuário pode esperar que novos caracteres substituam a entrada existente.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="f7c5b-109">O <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> e <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriedades permitem que você modificar o comportamento de acordo com sua finalidade.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="f7c5b-110">Controlar o ponto de inserção em um controle TextBox</span><span class="sxs-lookup"><span data-stu-id="f7c5b-110">To control the insertion point in a TextBox control</span></span>  
  
1.  <span data-ttu-id="f7c5b-111">Defina a propriedade <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="f7c5b-112">Zero coloca o ponto de inserção imediatamente à esquerda do primeiro caractere.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2.  <span data-ttu-id="f7c5b-113">(Opcional) Defina o <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriedade para o comprimento do texto que você deseja selecionar.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="f7c5b-114">O código abaixo sempre retorna o ponto de inserção para 0.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="f7c5b-115">O manipulador de eventos `TextBox1_Enter` deve ser associado ao controle; para obter mais informações, consulte [Criando manipuladores de eventos no Windows Forms](../creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f7c5b-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../creating-event-handlers-in-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="f7c5b-116">Tornando o ponto de inserção visível por padrão</span><span class="sxs-lookup"><span data-stu-id="f7c5b-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="f7c5b-117">O <xref:System.Windows.Forms.TextBox> ponto de inserção é visível por padrão em um novo formulário apenas se o <xref:System.Windows.Forms.TextBox> controle é o primeiro na ordem de tabulação.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="f7c5b-118">Caso contrário, o ponto de inserção aparecerá apenas se você conceder a <xref:System.Windows.Forms.TextBox> o foco do teclado ou mouse.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="f7c5b-119">Tornar a o ponto de inserção da caixa de texto visível por padrão em um novo formulário</span><span class="sxs-lookup"><span data-stu-id="f7c5b-119">To make the text box insertion point visible by default on a new form</span></span>  
  
-   <span data-ttu-id="f7c5b-120">Defina as <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade `0`.</span><span class="sxs-lookup"><span data-stu-id="f7c5b-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c5b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7c5b-121">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="f7c5b-122">Visão geral do controle TextBox</span><span class="sxs-lookup"><span data-stu-id="f7c5b-122">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="f7c5b-123">Como: Criar uma caixa de texto de senha com o controle TextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7c5b-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f7c5b-124">Como: Criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="f7c5b-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="f7c5b-125">Como: Inserir aspas em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f7c5b-125">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="f7c5b-126">Como: Selecionar texto no controle TextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7c5b-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f7c5b-127">Como: Exibir várias linhas no controle TextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7c5b-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f7c5b-128">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="f7c5b-128">TextBox Control</span></span>](textbox-control-windows-forms.md)
