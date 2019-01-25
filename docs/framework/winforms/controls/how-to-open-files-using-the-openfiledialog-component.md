---
title: 'Como: Abrir arquivos usando o componente OpenFileDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 87e7640da76205341b9e95310314800ac9dbfe30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678805"
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="941db-102">Como: Abrir arquivos usando o componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="941db-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="941db-103">O <xref:System.Windows.Forms.OpenFileDialog> componente permite que os usuários pesquisem as pastas do seu computador ou em qualquer computador na rede e selecione um ou mais arquivos para abrir.</span><span class="sxs-lookup"><span data-stu-id="941db-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="941db-104">A caixa de diálogo retorna o caminho e o nome do arquivo que o usuário selecionou na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="941db-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="941db-105">Depois que o usuário tiver selecionado o arquivo a ser aberto, há duas abordagens para o mecanismo de abertura do arquivo.</span><span class="sxs-lookup"><span data-stu-id="941db-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="941db-106">Se você preferir trabalhar com fluxos de arquivos, você pode criar uma instância da <xref:System.IO.StreamReader> classe.</span><span class="sxs-lookup"><span data-stu-id="941db-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="941db-107">Como alternativa, você pode usar o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para abrir o arquivo selecionado.</span><span class="sxs-lookup"><span data-stu-id="941db-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="941db-108">O primeiro exemplo a seguir envolve uma <xref:System.Security.Permissions.FileIOPermission> verificação de permissão (conforme descrito na "Observação de segurança" abaixo), mas fornece a você acesso ao nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="941db-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="941db-109">É possível usar essa técnica do Computador Local, da Intranet e zonas da Internet.</span><span class="sxs-lookup"><span data-stu-id="941db-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="941db-110">O segundo método também faz um <xref:System.Security.Permissions.FileIOPermission> verificação de permissão, mas é mais adequado para aplicativos nas zonas da Intranet ou Internet.</span><span class="sxs-lookup"><span data-stu-id="941db-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="941db-111">Abrir um arquivo como um fluxo usando o componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="941db-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="941db-112">Exiba a caixa de diálogo **Abrir Arquivo** e chame um método para abrir o arquivo selecionado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="941db-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="941db-113">Uma abordagem é usar o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo Abrir arquivo e usar uma instância da <xref:System.IO.StreamReader> classe para abrir o arquivo.</span><span class="sxs-lookup"><span data-stu-id="941db-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="941db-114">O exemplo a seguir usa o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos para abrir uma instância da <xref:System.Windows.Forms.OpenFileDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="941db-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="941db-115">Quando um arquivo é escolhido e o usuário clica em **OK**, o arquivo selecionado na caixa de diálogo será aberto.</span><span class="sxs-lookup"><span data-stu-id="941db-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="941db-116">Nesse caso, os conteúdos serão exibidos em uma caixa de mensagem, apenas para mostrar que o fluxo de arquivo foi lido.</span><span class="sxs-lookup"><span data-stu-id="941db-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="941db-117">Para obter ou definir a <xref:System.Windows.Forms.FileDialog.FileName%2A> propriedade, seu assembly requer um nível de privilégio concedido pela <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="941db-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="941db-118">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="941db-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="941db-119">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="941db-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="941db-120">O exemplo supõe que seu formulário tem um <xref:System.Windows.Forms.Button> controle e um <xref:System.Windows.Forms.OpenFileDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="941db-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
       }  
    ```  
  
     <span data-ttu-id="941db-121">(Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="941db-121">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="941db-122">Para obter mais informações sobre a leitura de fluxos de arquivos, consulte <xref:System.IO.FileStream.BeginRead%2A> e <xref:System.IO.FileStream.Read%2A>.</span><span class="sxs-lookup"><span data-stu-id="941db-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="941db-123">Abrir um arquivo como um arquivo usando o componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="941db-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="941db-124">Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo e o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para abrir o arquivo.</span><span class="sxs-lookup"><span data-stu-id="941db-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="941db-125">O <xref:System.Windows.Forms.OpenFileDialog> do componente <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método retorna os bytes que compõem o arquivo.</span><span class="sxs-lookup"><span data-stu-id="941db-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="941db-126">Esses bytes oferecem um fluxo de leitura.</span><span class="sxs-lookup"><span data-stu-id="941db-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="941db-127">No exemplo a seguir, uma <xref:System.Windows.Forms.OpenFileDialog> componente é instanciado com um filtro de "cursor", permitindo que o usuário escolher somente arquivos com a extensão de nome de arquivo`.cur`.</span><span class="sxs-lookup"><span data-stu-id="941db-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="941db-128">Se um arquivo `.cur` for escolhido, o cursor do formulário será definido como o cursor selecionado.</span><span class="sxs-lookup"><span data-stu-id="941db-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="941db-129">Para chamar o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método, seu assembly requer um nível de privilégio concedido pela <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="941db-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="941db-130">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="941db-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="941db-131">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="941db-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="941db-132">O exemplo supõe que seu formulário tem um <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="941db-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
       }  
    ```  
  
     <span data-ttu-id="941db-133">(Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="941db-133">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="941db-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="941db-134">See also</span></span>
- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="941db-135">Componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="941db-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
