---
title: Visão geral do controle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742797"
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="49f05-102">Visão geral do controle TextBox (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="49f05-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="49f05-103">Caixas de texto dos Windows Forms são usadas para obter entradas do usuário ou para exibir texto.</span><span class="sxs-lookup"><span data-stu-id="49f05-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="49f05-104">O controle <xref:System.Windows.Forms.TextBox> geralmente é usado para texto editável, embora também possa ser tornado somente leitura.</span><span class="sxs-lookup"><span data-stu-id="49f05-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="49f05-105">Caixas de texto podem exibir várias linhas, quebrar o texto para o tamanho do controle e adicionar formatação básica.</span><span class="sxs-lookup"><span data-stu-id="49f05-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="49f05-106">O controle <xref:System.Windows.Forms.TextBox> fornece um estilo de formato único para texto exibido ou inserido no controle.</span><span class="sxs-lookup"><span data-stu-id="49f05-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="49f05-107">Para exibir vários tipos de texto formatado, use o controle <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="49f05-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="49f05-108">Para obter mais informações, consulte [Visão geral do controle RichTextBox](richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="49f05-108">For more information, see [RichTextBox Control Overview](richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="49f05-109">Trabalhando com o controle TextBox</span><span class="sxs-lookup"><span data-stu-id="49f05-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="49f05-110">O texto exibido pelo controle está contido na propriedade <xref:System.Windows.Forms.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="49f05-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="49f05-111">Por padrão, você pode inserir até 2048 caracteres em uma caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="49f05-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="49f05-112">Se você definir a propriedade <xref:System.Windows.Forms.TextBox.Multiline%2A> como `true`, poderá inserir até 32 KB de texto.</span><span class="sxs-lookup"><span data-stu-id="49f05-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="49f05-113">A propriedade <xref:System.Windows.Forms.TextBox.Text%2A> pode ser definida em tempo de design com a janela Propriedades, em tempo de execução no código ou pela entrada do usuário em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="49f05-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="49f05-114">O conteúdo atual de uma caixa de texto pode ser recuperado em tempo de execução, lendo a propriedade <xref:System.Windows.Forms.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="49f05-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="49f05-115">O exemplo de código a seguir define o texto no controle no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="49f05-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="49f05-116">O procedimento de `InitializeMyControl` não será executado automaticamente; Ele deve ser chamado.</span><span class="sxs-lookup"><span data-stu-id="49f05-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="49f05-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="49f05-117">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="49f05-118">Como controlar o ponto de inserção em um controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49f05-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="49f05-119">Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49f05-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="49f05-120">Como criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="49f05-120">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="49f05-121">Como inserir aspas em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="49f05-121">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="49f05-122">Como selecionar texto no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49f05-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="49f05-123">Como exibir várias linhas no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49f05-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="49f05-124">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="49f05-124">TextBox Control</span></span>](textbox-control-windows-forms.md)
