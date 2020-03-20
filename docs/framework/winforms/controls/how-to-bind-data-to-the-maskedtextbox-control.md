---
title: Como associar dados ao controle MaskedTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
- data binding [Windows Forms], MaskedTextBox control [Windows Forms]
- MaskedTextBox control [Windows Forms], binding data
ms.assetid: 34b29f07-e8df-48d4-b08b-53fcca524708
ms.openlocfilehash: 0cbb239e24b254c37c453486590185e934adf482
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142167"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a><span data-ttu-id="dc656-102">Como associar dados ao controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="dc656-102">How to: Bind Data to the MaskedTextBox Control</span></span>
<span data-ttu-id="dc656-103">Você pode vincular <xref:System.Windows.Forms.MaskedTextBox> dados a um controle da forma como você pode a qualquer outro controle do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dc656-103">You can bind data to a <xref:System.Windows.Forms.MaskedTextBox> control just as you can to any other Windows Forms control.</span></span> <span data-ttu-id="dc656-104">No entanto, se o formato dos seus dados no banco de dados não corresponder ao formato esperado pela sua definição de máscara, será necessário reformatar os dados.</span><span class="sxs-lookup"><span data-stu-id="dc656-104">However, if the format of your data in the database does not match the format expected by your mask definition, you will need to reformat the data.</span></span> <span data-ttu-id="dc656-105">O procedimento a seguir demonstra <xref:System.Windows.Forms.Binding.Format> como <xref:System.Windows.Forms.Binding.Parse> fazer <xref:System.Windows.Forms.Binding> isso usando os eventos da classe para exibir os campos de banco de dados de número de telefone e extensão telefônica separados como um único campo editável.</span><span class="sxs-lookup"><span data-stu-id="dc656-105">The following procedure demonstrates how to do this using the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events of the <xref:System.Windows.Forms.Binding> class to display separate phone number and phone extension database fields as a single editable field.</span></span>  
  
 <span data-ttu-id="dc656-106">O procedimento a seguir requer que você tenha acesso a um banco de dados do SQL Server com o banco de dados Northwind de exemplo instalado.</span><span class="sxs-lookup"><span data-stu-id="dc656-106">The following procedure requires that you have access to a SQL Server database with the Northwind sample database installed.</span></span>  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a><span data-ttu-id="dc656-107">Associar dados ao controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="dc656-107">To bind data to a MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="dc656-108">Criar um novo projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dc656-108">Create a new Windows Forms project.</span></span>  
  
2. <span data-ttu-id="dc656-109">Arraste <xref:System.Windows.Forms.TextBox> dois controles para o seu formulário; nomeá-los `FirstName` e `LastName`.</span><span class="sxs-lookup"><span data-stu-id="dc656-109">Drag two <xref:System.Windows.Forms.TextBox> controls onto your form; name them `FirstName` and `LastName`.</span></span>  
  
3. <span data-ttu-id="dc656-110">Arraste <xref:System.Windows.Forms.MaskedTextBox> um controle para o seu formulário; nomeá-lo `PhoneMask`.</span><span class="sxs-lookup"><span data-stu-id="dc656-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control onto your form; name it `PhoneMask`.</span></span>  
  
4. <span data-ttu-id="dc656-111">Defina <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> a `PhoneMask` `(000) 000-0000 x9999`propriedade de .</span><span class="sxs-lookup"><span data-stu-id="dc656-111">Set the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of `PhoneMask` to `(000) 000-0000 x9999`.</span></span>  
  
5. <span data-ttu-id="dc656-112">Adicione as seguintes importações de namespace ao formulário.</span><span class="sxs-lookup"><span data-stu-id="dc656-112">Add the following namespace imports to the form.</span></span>  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6. <span data-ttu-id="dc656-113">Clique com o botão direito do mouse no formulário e escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="dc656-113">Right-click the form and choose **View Code**.</span></span> <span data-ttu-id="dc656-114">Coloque esse código em qualquer lugar em sua classe de formulário.</span><span class="sxs-lookup"><span data-stu-id="dc656-114">Place this code anywhere in your form class.</span></span>  
  
    ```csharp  
    Binding currentBinding, phoneBinding;  
    DataSet employeesTable = new DataSet();  
    SqlConnection sc;  
    SqlDataAdapter dataConnect;  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        DoMaskBinding();  
    }  
  
    private void DoMaskBinding()  
    {  
        try  
        {  
            sc = new SqlConnection("Data Source=CLIENTUE;Initial Catalog=NORTHWIND;Integrated Security=SSPI");  
            sc.Open();  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
  
        dataConnect = new SqlDataAdapter("SELECT * FROM Employees", sc);  
        dataConnect.Fill(employeesTable, "Employees");  
  
        // Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        // before adding them to the control - otherwise, we won't get a Format event on the
        // initial load.
        try  
        {  
            currentBinding = new Binding("Text", employeesTable, "Employees.FirstName");  
            firstName.DataBindings.Add(currentBinding);  
  
            currentBinding = new Binding("Text", employeesTable, "Employees.LastName");  
            lastName.DataBindings.Add(currentBinding);  
  
            phoneBinding =new Binding("Text", employeesTable, "Employees.HomePhone");  
            // We must add the event handlers before we bind, or the Format event will not get called  
            // for the first record.  
            phoneBinding.Format += new ConvertEventHandler(phoneBinding_Format);  
            phoneBinding.Parse += new ConvertEventHandler(phoneBinding_Parse);  
            phoneMask.DataBindings.Add(phoneBinding);  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
    }  
    ```  
  
    ```vb  
    Dim WithEvents CurrentBinding, PhoneBinding As Binding  
    Dim EmployeesTable As New DataSet()  
    Dim sc As SqlConnection  
    Dim DataConnect As SqlDataAdapter  
  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        DoMaskedBinding()  
    End Sub  
  
    Private Sub DoMaskedBinding()  
        Try  
            sc = New SqlConnection("Data Source=SERVERNAME;Initial Catalog=NORTHWIND;Integrated Security=SSPI")  
            sc.Open()  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Exit Sub  
        End Try  
  
        DataConnect = New SqlDataAdapter("SELECT * FROM Employees", sc)  
        DataConnect.Fill(EmployeesTable, "Employees")  
  
        ' Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        ' before adding them to the control - otherwise, we won't get a Format event on the
        ' initial load.  
        Try  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.FirstName")  
            firstName.DataBindings.Add(CurrentBinding)  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.LastName")  
            lastName.DataBindings.Add(CurrentBinding)  
            PhoneBinding = New Binding("Text", EmployeesTable, "Employees.HomePhone")  
            PhoneMask.DataBindings.Add(PhoneBinding)  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Application.Exit()  
        End Try  
    End Sub  
    ```  
  
7. <span data-ttu-id="dc656-115">Adicione manipuladores de <xref:System.Windows.Forms.Binding.Format> <xref:System.Windows.Forms.Binding.Parse> eventos para os `PhoneNumber` eventos `Extension` e combinar <xref:System.Data.DataSet>e separar os campos e os campos do limite .</span><span class="sxs-lookup"><span data-stu-id="dc656-115">Add event handlers for the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events to combine and separate the `PhoneNumber` and `Extension` fields from the bound <xref:System.Data.DataSet>.</span></span>  
  
    ```csharp  
    private void phoneBinding_Format(Object sender, ConvertEventArgs e)  
    {  
        String ext;  
  
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        if (currentRow["Extension"] == null)
        {  
            ext = "";  
        } else
        {  
            ext = currentRow["Extension"].ToString();  
        }  
  
        e.Value = e.Value.ToString().Trim() + " x" + ext;  
    }  
  
    private void phoneBinding_Parse(Object sender, ConvertEventArgs e)  
    {  
        String phoneNumberAndExt = e.Value.ToString();  
  
        int extIndex = phoneNumberAndExt.IndexOf("x");  
        String ext = phoneNumberAndExt.Substring(extIndex).Trim();  
        String phoneNumber = phoneNumberAndExt.Substring(0, extIndex).Trim();  
  
        //Get the current binding object, and set the new extension manually.
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        // Remove the "x" from the extension.  
        currentRow["Extension"] = ext.Substring(1);  
  
        //Return the phone number.  
        e.Value = phoneNumber;  
    }  
    ```  
  
    ```vb  
    Private Sub PhoneBinding_Format(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Format  
        Dim Ext As String  
  
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        If (CurrentRow("Extension") Is Nothing) Then  
            Ext = ""  
        Else  
            Ext = CurrentRow("Extension").ToString()  
        End If  
  
        e.Value = e.Value.ToString().Trim() & " x" & Ext  
    End Sub  
  
    Private Sub PhoneBinding_Parse(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Parse  
        Dim PhoneNumberAndExt As String = e.Value.ToString()  
  
        Dim ExtIndex As Integer = PhoneNumberAndExt.IndexOf("x")  
        Dim Ext As String = PhoneNumberAndExt.Substring(ExtIndex).Trim()  
        Dim PhoneNumber As String = PhoneNumberAndExt.Substring(0, ExtIndex).Trim()  
  
        ' Get the current binding object, and set the new extension manually.
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        ' Remove the "x" from the extension.  
        CurrentRow("Extension") = CObj(Ext.Substring(1))  
  
        ' Return the phone number.  
        e.Value = PhoneNumber  
    End Sub  
    ```  
  
8. <span data-ttu-id="dc656-116">Adicione <xref:System.Windows.Forms.Button> dois controles ao formulário.</span><span class="sxs-lookup"><span data-stu-id="dc656-116">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span> <span data-ttu-id="dc656-117">Nomeie-os `previousButton` e `nextButton`.</span><span class="sxs-lookup"><span data-stu-id="dc656-117">Name them `previousButton` and `nextButton`.</span></span> <span data-ttu-id="dc656-118">Clique duas vezes em <xref:System.Windows.Forms.Control.Click> cada botão para adicionar um manipulador de eventos e preencha os manipuladores de eventos, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="dc656-118">Double-click each button to add a <xref:System.Windows.Forms.Control.Click> event handler, and fill in the event handlers as shown in the following code example.</span></span>  
  
    ```csharp  
    private void previousButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position - 1;  
    }  
  
    private void nextButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position + 1;  
    }  
    ```  
  
    ```vb  
    Private Sub PreviousButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles PreviousButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position - 1  
    End Sub  
  
    Private Sub NextButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles NextButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position + 1  
    End Sub  
    ```  
  
9. <span data-ttu-id="dc656-119">Execute o exemplo.</span><span class="sxs-lookup"><span data-stu-id="dc656-119">Run the sample.</span></span> <span data-ttu-id="dc656-120">Edite os dados e use os botões **Anterior** e **Seguinte** para <xref:System.Data.DataSet>ver se os dados são adequadamente persistidos para o .</span><span class="sxs-lookup"><span data-stu-id="dc656-120">Edit the data, and use the **Previous** and **Next** buttons to see that the data is properly persisted to the <xref:System.Data.DataSet>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc656-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc656-121">Example</span></span>  
 <span data-ttu-id="dc656-122">O exemplo de código a seguir é a lista de código completa resultante da conclusão do procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="dc656-122">The following code example is the full code listing that results from completing the previous procedure.</span></span>  
  
 [!code-cpp[MaskedTextBoxData#1](~/samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](~/samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dc656-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="dc656-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="dc656-124">Crie um projeto Visual C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dc656-124">Create a Visual C# or Visual Basic project.</span></span>  
  
- <span data-ttu-id="dc656-125">Adicione <xref:System.Windows.Forms.TextBox> os <xref:System.Windows.Forms.MaskedTextBox> controles e controles ao formulário, conforme descrito no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="dc656-125">Add the <xref:System.Windows.Forms.TextBox> and <xref:System.Windows.Forms.MaskedTextBox> controls to the form, as described in the previous procedure.</span></span>  
  
- <span data-ttu-id="dc656-126">Abra o arquivo de código-fonte para o formulário de padrão do projeto.</span><span class="sxs-lookup"><span data-stu-id="dc656-126">Open the source code file for the project's default form.</span></span>  
  
- <span data-ttu-id="dc656-127">Substitua o código-fonte deste arquivo pelo código listado na seção “Código” anterior.</span><span class="sxs-lookup"><span data-stu-id="dc656-127">Replace the source code in this file with the code listed in the previous "Code" section.</span></span>  
  
- <span data-ttu-id="dc656-128">Compile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc656-128">Compile the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc656-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="dc656-129">See also</span></span>

- [<span data-ttu-id="dc656-130">Passo a passo: trabalhando com o controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="dc656-130">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
