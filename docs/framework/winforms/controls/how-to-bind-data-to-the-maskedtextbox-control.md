---
title: 'Como: Associar dados ao controle MaskedTextBox'
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
ms.openlocfilehash: f10a19433c70eb0a1dacf99925f70d6796727da9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612414"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a><span data-ttu-id="86b91-102">Como: Associar dados ao controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="86b91-102">How to: Bind Data to the MaskedTextBox Control</span></span>
<span data-ttu-id="86b91-103">Você pode associar dados a um <xref:System.Windows.Forms.MaskedTextBox> controlar exatamente como faria para qualquer outro controle de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="86b91-103">You can bind data to a <xref:System.Windows.Forms.MaskedTextBox> control just as you can to any other Windows Forms control.</span></span> <span data-ttu-id="86b91-104">No entanto, se o formato dos seus dados no banco de dados não corresponder ao formato esperado pela sua definição de máscara, será necessário reformatar os dados.</span><span class="sxs-lookup"><span data-stu-id="86b91-104">However, if the format of your data in the database does not match the format expected by your mask definition, you will need to reformat the data.</span></span> <span data-ttu-id="86b91-105">O procedimento a seguir demonstra como fazer isso usando o <xref:System.Windows.Forms.Binding.Format> e <xref:System.Windows.Forms.Binding.Parse> eventos do <xref:System.Windows.Forms.Binding> classe para exibir o número de telefone separados e campos de banco de dados de extensão de telefone como um único campo editável.</span><span class="sxs-lookup"><span data-stu-id="86b91-105">The following procedure demonstrates how to do this using the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events of the <xref:System.Windows.Forms.Binding> class to display separate phone number and phone extension database fields as a single editable field.</span></span>  
  
 <span data-ttu-id="86b91-106">O procedimento a seguir requer que você tenha acesso a um banco de dados do SQL Server com o banco de dados Northwind de exemplo instalado.</span><span class="sxs-lookup"><span data-stu-id="86b91-106">The following procedure requires that you have access to a SQL Server database with the Northwind sample database installed.</span></span>  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a><span data-ttu-id="86b91-107">Associar dados ao controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="86b91-107">To bind data to a MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="86b91-108">Criar um novo projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="86b91-108">Create a new Windows Forms project.</span></span>  
  
2. <span data-ttu-id="86b91-109">Arraste duas <xref:System.Windows.Forms.TextBox> controles para seu formulário; nomeie-as `FirstName` e `LastName`.</span><span class="sxs-lookup"><span data-stu-id="86b91-109">Drag two <xref:System.Windows.Forms.TextBox> controls onto your form; name them `FirstName` and `LastName`.</span></span>  
  
3. <span data-ttu-id="86b91-110">Arraste uma <xref:System.Windows.Forms.MaskedTextBox> de controle para seu formulário; nomeie- `PhoneMask`.</span><span class="sxs-lookup"><span data-stu-id="86b91-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control onto your form; name it `PhoneMask`.</span></span>  
  
4. <span data-ttu-id="86b91-111">Defina as <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade de `PhoneMask` para `(000) 000-0000 x9999`.</span><span class="sxs-lookup"><span data-stu-id="86b91-111">Set the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of `PhoneMask` to `(000) 000-0000 x9999`.</span></span>  
  
5. <span data-ttu-id="86b91-112">Adicione as seguintes importações de namespace ao formulário.</span><span class="sxs-lookup"><span data-stu-id="86b91-112">Add the following namespace imports to the form.</span></span>  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6. <span data-ttu-id="86b91-113">Clique com o botão direito do mouse do formulário e escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="86b91-113">Right-click the form and choose **View Code**.</span></span> <span data-ttu-id="86b91-114">Coloque esse código em qualquer lugar em sua classe de formulário.</span><span class="sxs-lookup"><span data-stu-id="86b91-114">Place this code anywhere in your form class.</span></span>  
  
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
  
7. <span data-ttu-id="86b91-115">Adicionar manipuladores de eventos para o <xref:System.Windows.Forms.Binding.Format> e <xref:System.Windows.Forms.Binding.Parse> eventos para combinar e separar o `PhoneNumber` e `Extension` campos base no limite <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="86b91-115">Add event handlers for the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events to combine and separate the `PhoneNumber` and `Extension` fields from the bound <xref:System.Data.DataSet>.</span></span>  
  
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
  
8. <span data-ttu-id="86b91-116">Adicione dois <xref:System.Windows.Forms.Button> controles ao formulário.</span><span class="sxs-lookup"><span data-stu-id="86b91-116">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span> <span data-ttu-id="86b91-117">Nomeie-os como `previousButton` e `nextButton`.</span><span class="sxs-lookup"><span data-stu-id="86b91-117">Name them `previousButton` and `nextButton`.</span></span> <span data-ttu-id="86b91-118">Clique duas vezes em cada botão para adicionar um <xref:System.Windows.Forms.Control.Click> manipulador de eventos e preencha os manipuladores de eventos, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="86b91-118">Double-click each button to add a <xref:System.Windows.Forms.Control.Click> event handler, and fill in the event handlers as shown in the following code example.</span></span>  
  
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
  
9. <span data-ttu-id="86b91-119">Executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="86b91-119">Run the sample.</span></span> <span data-ttu-id="86b91-120">Edite os dados e use o **Previous** e **próxima** botões para ver o que os dados são mantidos corretamente o <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="86b91-120">Edit the data, and use the **Previous** and **Next** buttons to see that the data is properly persisted to the <xref:System.Data.DataSet>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86b91-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86b91-121">Example</span></span>  
 <span data-ttu-id="86b91-122">O exemplo de código a seguir é a lista de código completa resultante da conclusão do procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="86b91-122">The following code example is the full code listing that results from completing the previous procedure.</span></span>  
  
 [!code-cpp[MaskedTextBoxData#1](~/samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](~/samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="86b91-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="86b91-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="86b91-124">Criar um Visual C# ou o projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86b91-124">Create a Visual C# or Visual Basic project.</span></span>  
  
- <span data-ttu-id="86b91-125">Adicione a <xref:System.Windows.Forms.TextBox> e <xref:System.Windows.Forms.MaskedTextBox> controles ao formulário, conforme descrito no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="86b91-125">Add the <xref:System.Windows.Forms.TextBox> and <xref:System.Windows.Forms.MaskedTextBox> controls to the form, as described in the previous procedure.</span></span>  
  
- <span data-ttu-id="86b91-126">Abra o arquivo de código-fonte para o formulário de padrão do projeto.</span><span class="sxs-lookup"><span data-stu-id="86b91-126">Open the source code file for the project's default form.</span></span>  
  
- <span data-ttu-id="86b91-127">Substitua o código-fonte deste arquivo pelo código listado na seção “Código” anterior.</span><span class="sxs-lookup"><span data-stu-id="86b91-127">Replace the source code in this file with the code listed in the previous "Code" section.</span></span>  
  
- <span data-ttu-id="86b91-128">Compile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86b91-128">Compile the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b91-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86b91-129">See also</span></span>

- [<span data-ttu-id="86b91-130">Passo a passo: Trabalhando com o controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="86b91-130">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
