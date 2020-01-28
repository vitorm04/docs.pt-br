---
title: Criar uma caixa de texto de senha com controle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: ff4706a736d15f14cf437c808219e9088773dc6d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731285"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="10772-102">Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="10772-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>

<span data-ttu-id="10772-103">Uma caixa de senha é uma caixa de texto do Windows Forms que exibe caracteres de espaço reservado enquanto um usuário digita uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="10772-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>

### <a name="to-create-a-password-text-box"></a><span data-ttu-id="10772-104">Criar uma caixa de texto de senha</span><span class="sxs-lookup"><span data-stu-id="10772-104">To create a password text box</span></span>

1. <span data-ttu-id="10772-105">Defina a propriedade <xref:System.Windows.Forms.TextBox.PasswordChar%2A> do controle de <xref:System.Windows.Forms.TextBox> como um caractere específico.</span><span class="sxs-lookup"><span data-stu-id="10772-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>

    <span data-ttu-id="10772-106">A propriedade <xref:System.Windows.Forms.TextBox.PasswordChar%2A> especifica o caractere exibido na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="10772-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="10772-107">Por exemplo, se você quiser que os asteriscos sejam exibidos na caixa senha, especifique \* para a propriedade <xref:System.Windows.Forms.TextBox.PasswordChar%2A> na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="10772-107">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="10772-108">Em seguida, independentemente de qual caractere de um usuário digita na caixa de texto, será exibido um asterisco.</span><span class="sxs-lookup"><span data-stu-id="10772-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>

2. <span data-ttu-id="10772-109">Adicional Defina a propriedade <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>.</span><span class="sxs-lookup"><span data-stu-id="10772-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="10772-110">A propriedade determina quantos caracteres podem ser digitado na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="10772-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="10772-111">Se o tamanho máximo for excedido, o sistema emitirá um aviso sonoro e a caixa de texto não aceitará mais caracteres.</span><span class="sxs-lookup"><span data-stu-id="10772-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="10772-112">Observe que isso pode não ser recomendável, visto que o tamanho máximo de uma senha pode ser útil para os hackers que estão tentando adivinhá-la.</span><span class="sxs-lookup"><span data-stu-id="10772-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>

    <span data-ttu-id="10772-113">O exemplo de código a seguir mostra como inicializar uma caixa de texto que aceita uma cadeia de até 14 caracteres e exibir os asteriscos no lugar da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="10772-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="10772-114">O procedimento de `InitializeMyControl` não será executado automaticamente; Ele deve ser chamado.</span><span class="sxs-lookup"><span data-stu-id="10772-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="10772-115">Usar a propriedade <xref:System.Windows.Forms.TextBox.PasswordChar%2A> em uma caixa de texto pode ajudar a garantir que outras pessoas não poderão determinar a senha de um usuário se observarem o usuário inserindo-a.</span><span class="sxs-lookup"><span data-stu-id="10772-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="10772-116">Essa medida de segurança não abrange nenhum tipo de armazenamento e transmissão de senha que pode ocorrer devido a lógica do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10772-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="10772-117">Como o texto inserido não é criptografado de nenhuma forma, você deve tratá-lo como qualquer outro dado confidencial.</span><span class="sxs-lookup"><span data-stu-id="10772-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="10772-118">Mesmo que ela não apareça como tal, a senha é ainda está sendo tratada como uma cadeia de caracteres de texto sem formatação (a menos que você implemente alguma outra medida de segurança adicional).</span><span class="sxs-lookup"><span data-stu-id="10772-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>

    ```vb
    Private Sub InitializeMyControl()
       ' Set to no text.
       TextBox1.Text = ""
       ' The password character is an asterisk.
       TextBox1.PasswordChar = "*"
       ' The control will allow no more than 14 characters.
       TextBox1.MaxLength = 14
    End Sub
    ```

    ```csharp
    private void InitializeMyControl()
    {
       // Set to no text.
       textBox1.Text = "";
       // The password character is an asterisk.
       textBox1.PasswordChar = '*';
       // The control will allow no more than 14 characters.
       textBox1.MaxLength = 14;
    }
    ```

    ```cpp
    private:
       void InitializeMyControl()
       {
          // Set to no text.
          textBox1->Text = "";
          // The password character is an asterisk.
          textBox1->PasswordChar = '*';
          // The control will allow no more than 14 characters.
          textBox1->MaxLength = 14;
       }
    ```

## <a name="see-also"></a><span data-ttu-id="10772-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="10772-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="10772-120">Visão geral do controle TextBox</span><span class="sxs-lookup"><span data-stu-id="10772-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="10772-121">Como controlar o ponto de inserção em um controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="10772-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="10772-122">Como criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="10772-122">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="10772-123">Como inserir aspas em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="10772-123">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="10772-124">Como selecionar texto no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="10772-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="10772-125">Como exibir várias linhas no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="10772-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="10772-126">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="10772-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
