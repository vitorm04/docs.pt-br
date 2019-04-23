---
title: 'Como: Criar uma caixa de texto de senha com o controle TextBox do Windows Forms'
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
ms.openlocfilehash: ab5df1233c16a7ce076efa817fb14808b588ebcd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300977"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="1d332-102">Como: Criar uma caixa de texto de senha com o controle TextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d332-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>
<span data-ttu-id="1d332-103">Uma caixa de senha é uma caixa de texto do Windows Forms que exibe caracteres de espaço reservado enquanto um usuário digita uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1d332-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>  
  
### <a name="to-create-a-password-text-box"></a><span data-ttu-id="1d332-104">Criar uma caixa de texto de senha</span><span class="sxs-lookup"><span data-stu-id="1d332-104">To create a password text box</span></span>  
  
1. <span data-ttu-id="1d332-105">Defina as <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriedade do <xref:System.Windows.Forms.TextBox> controle a um caractere específico.</span><span class="sxs-lookup"><span data-stu-id="1d332-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>  
  
     <span data-ttu-id="1d332-106">O <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriedade especifica o caractere exibido na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="1d332-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="1d332-107">Por exemplo, se você quiser que asteriscos sejam exibidos na caixa de senha, especifique \* para o <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriedade na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="1d332-107">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="1d332-108">Em seguida, independentemente de qual caractere de um usuário digita na caixa de texto, será exibido um asterisco.</span><span class="sxs-lookup"><span data-stu-id="1d332-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>  
  
2. <span data-ttu-id="1d332-109">(Opcional) Defina o <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1d332-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="1d332-110">A propriedade determina quantos caracteres podem ser digitado na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="1d332-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="1d332-111">Se o tamanho máximo for excedido, o sistema emitirá um aviso sonoro e a caixa de texto não aceitará mais caracteres.</span><span class="sxs-lookup"><span data-stu-id="1d332-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="1d332-112">Observe que isso pode não ser recomendável, visto que o tamanho máximo de uma senha pode ser útil para os hackers que estão tentando adivinhá-la.</span><span class="sxs-lookup"><span data-stu-id="1d332-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>  
  
     <span data-ttu-id="1d332-113">O exemplo de código a seguir mostra como inicializar uma caixa de texto que aceita uma cadeia de até 14 caracteres e exibir os asteriscos no lugar da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1d332-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="1d332-114">O `InitializeMyControl` procedimento não será executado automaticamente; ele deve ser chamado.</span><span class="sxs-lookup"><span data-stu-id="1d332-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1d332-115">Usando o <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriedade em uma caixa de texto pode ajudar a garantir que outras pessoas não poderão determinar uma senha de usuário se eles observarem o usuário inseri-la.</span><span class="sxs-lookup"><span data-stu-id="1d332-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="1d332-116">Essa medida de segurança não abrange nenhum tipo de armazenamento e transmissão de senha que pode ocorrer devido a lógica do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d332-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="1d332-117">Como o texto inserido não é criptografado de nenhuma forma, você deve tratá-lo como qualquer outro dado confidencial.</span><span class="sxs-lookup"><span data-stu-id="1d332-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="1d332-118">Mesmo que ela não apareça como tal, a senha é ainda está sendo tratada como uma cadeia de caracteres de texto sem formatação (a menos que você implemente alguma outra medida de segurança adicional).</span><span class="sxs-lookup"><span data-stu-id="1d332-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d332-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d332-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="1d332-120">Visão geral do controle TextBox</span><span class="sxs-lookup"><span data-stu-id="1d332-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="1d332-121">Como: Controlar o ponto de inserção em um controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d332-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="1d332-122">Como: Criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="1d332-122">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="1d332-123">Como: Inserir aspas em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1d332-123">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="1d332-124">Como: Selecione o texto no controle TextBox de formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="1d332-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="1d332-125">Como: Exibir várias linhas no controle TextBox de formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="1d332-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="1d332-126">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="1d332-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
