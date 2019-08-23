---
title: 'Como: Colocar aspas em uma cadeia de caracteres (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 20828f75eeae9df33fcc22d8558b26a8a1ab2bdc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910430"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="4b296-102">Como: Colocar aspas em uma cadeia de caracteres (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4b296-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="4b296-103">Às vezes, você pode querer colocar aspas (" ") em uma cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="4b296-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="4b296-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4b296-104">For example:</span></span>  
  
 <span data-ttu-id="4b296-105">Ela disse: "Você merece um agrado!"</span><span class="sxs-lookup"><span data-stu-id="4b296-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="4b296-106">Como alternativa, você também pode usar o <xref:Microsoft.VisualBasic.ControlChars.Quote> campo como uma constante.</span><span class="sxs-lookup"><span data-stu-id="4b296-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="4b296-107">Para colocar as aspas em uma cadeia de caracteres no código</span><span class="sxs-lookup"><span data-stu-id="4b296-107">To place quotation marks in a string in your code</span></span>  
  
1. <span data-ttu-id="4b296-108">Em Visual Basic, insira duas aspas em uma linha como uma aspa incorporada.</span><span class="sxs-lookup"><span data-stu-id="4b296-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="4b296-109">No Visual C# e Visual C++, insira a sequência \\de escape "como uma aspa incorporada.</span><span class="sxs-lookup"><span data-stu-id="4b296-109">In Visual C# and Visual C++, insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="4b296-110">Por exemplo, para criar a cadeia de caracteres anterior, use o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b296-110">For example, to create the preceding string, use the following code.</span></span>  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     <span data-ttu-id="4b296-111">- ou -</span><span class="sxs-lookup"><span data-stu-id="4b296-111">-or-</span></span>  
  
2. <span data-ttu-id="4b296-112">Insira o caractere ASCII ou Unicode para aspas.</span><span class="sxs-lookup"><span data-stu-id="4b296-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="4b296-113">Em Visual Basic, use o caractere ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="4b296-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="4b296-114">No Visual C#, use o caractere Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="4b296-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="4b296-115">Neste exemplo, não é possível usar \u0022 porque você não pode usar um nome de caractere universal que designa um caractere no conjunto de caracteres básicos.</span><span class="sxs-lookup"><span data-stu-id="4b296-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="4b296-116">Caso contrário, você produz C3851.</span><span class="sxs-lookup"><span data-stu-id="4b296-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="4b296-117">Para obter mais informações, consulte [Erro do compilador C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="4b296-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="4b296-118">- ou -</span><span class="sxs-lookup"><span data-stu-id="4b296-118">-or-</span></span>  
  
3. <span data-ttu-id="4b296-119">Você também pode definir uma constante para o caractere e usá-la quando necessário.</span><span class="sxs-lookup"><span data-stu-id="4b296-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4b296-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b296-120">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="4b296-121">Visão geral do controle TextBox</span><span class="sxs-lookup"><span data-stu-id="4b296-121">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="4b296-122">Como: Controlar o ponto de inserção em um controle de caixa de texto Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b296-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="4b296-123">Como: Criar uma caixa de texto de senha com o controle caixa de texto Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b296-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4b296-124">Como: Criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="4b296-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="4b296-125">Como: Selecionar texto no controle de caixa de texto Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b296-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4b296-126">Como: Exibir várias linhas no controle de caixa de texto Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b296-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4b296-127">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="4b296-127">TextBox Control</span></span>](textbox-control-windows-forms.md)
