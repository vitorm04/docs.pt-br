---
title: Como abrir arquivos usando o componente OpenFileDialog
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
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fabe176ade1ae94a20100162ab7ab6fadfb2999f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="85bc1-102">Como abrir arquivos usando o componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="85bc1-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="85bc1-103">O <xref:System.Windows.Forms.OpenFileDialog> componente permite que os usuários procurar as pastas do seu computador ou de qualquer computador na rede e selecionar um ou mais arquivos para abrir.</span><span class="sxs-lookup"><span data-stu-id="85bc1-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="85bc1-104">A caixa de diálogo retorna o caminho e o nome do arquivo que o usuário selecionou na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="85bc1-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="85bc1-105">Depois que o usuário tiver selecionado o arquivo a ser aberto, há duas abordagens para o mecanismo de abertura do arquivo.</span><span class="sxs-lookup"><span data-stu-id="85bc1-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="85bc1-106">Se você preferir trabalhar com fluxos de arquivos, você pode criar uma instância do <xref:System.IO.StreamReader> classe.</span><span class="sxs-lookup"><span data-stu-id="85bc1-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="85bc1-107">Como alternativa, você pode usar o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para abrir o arquivo selecionado.</span><span class="sxs-lookup"><span data-stu-id="85bc1-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="85bc1-108">O primeiro exemplo abaixo envolve um <xref:System.Security.Permissions.FileIOPermission> verificação de permissão (conforme descrito em "Observação de segurança" abaixo), mas oferece acesso para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="85bc1-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="85bc1-109">É possível usar essa técnica do Computador Local, da Intranet e zonas da Internet.</span><span class="sxs-lookup"><span data-stu-id="85bc1-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="85bc1-110">O segundo método também faz uma <xref:System.Security.Permissions.FileIOPermission> verificação de permissão, mas é mais adequado para aplicativos em zonas da Internet ou Intranet.</span><span class="sxs-lookup"><span data-stu-id="85bc1-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="85bc1-111">Abrir um arquivo como um fluxo usando o componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="85bc1-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="85bc1-112">Exiba a caixa de diálogo **Abrir Arquivo** e chame um método para abrir o arquivo selecionado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="85bc1-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="85bc1-113">Uma abordagem é usar o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo Abrir arquivo e usar uma instância do <xref:System.IO.StreamReader> classe para abrir o arquivo.</span><span class="sxs-lookup"><span data-stu-id="85bc1-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="85bc1-114">O exemplo abaixo usa o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos para abrir uma instância do <xref:System.Windows.Forms.OpenFileDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="85bc1-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="85bc1-115">Quando um arquivo é escolhido e o usuário clica em **OK**, o arquivo selecionado na caixa de diálogo será aberto.</span><span class="sxs-lookup"><span data-stu-id="85bc1-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="85bc1-116">Nesse caso, os conteúdos serão exibidos em uma caixa de mensagem, apenas para mostrar que o fluxo de arquivo foi lido.</span><span class="sxs-lookup"><span data-stu-id="85bc1-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="85bc1-117">Para obter ou definir o <xref:System.Windows.Forms.FileDialog.FileName%2A> propriedade, seu assembly requer um nível de privilégio concedido pelo <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="85bc1-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="85bc1-118">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="85bc1-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="85bc1-119">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="85bc1-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="85bc1-120">O exemplo supõe que o formulário tem uma <xref:System.Windows.Forms.Button> controle e um <xref:System.Windows.Forms.OpenFileDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="85bc1-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="85bc1-121">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="85bc1-121">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="85bc1-122">Para obter mais informações sobre a leitura de fluxos de arquivos, consulte <xref:System.IO.FileStream.BeginRead%2A> e <xref:System.IO.FileStream.Read%2A>.</span><span class="sxs-lookup"><span data-stu-id="85bc1-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="85bc1-123">Abrir um arquivo como um arquivo usando o componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="85bc1-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="85bc1-124">Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo e o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para abrir o arquivo.</span><span class="sxs-lookup"><span data-stu-id="85bc1-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="85bc1-125">O <xref:System.Windows.Forms.OpenFileDialog> do componente <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método retorna os bytes que compõem o arquivo.</span><span class="sxs-lookup"><span data-stu-id="85bc1-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="85bc1-126">Esses bytes oferecem um fluxo de leitura.</span><span class="sxs-lookup"><span data-stu-id="85bc1-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="85bc1-127">No exemplo a seguir, uma <xref:System.Windows.Forms.OpenFileDialog> componente é instanciado com um filtro de "cursor", permitindo que o usuário escolha somente arquivos com a extensão de nome de arquivo`.cur`.</span><span class="sxs-lookup"><span data-stu-id="85bc1-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="85bc1-128">Se um arquivo `.cur` for escolhido, o cursor do formulário será definido como o cursor selecionado.</span><span class="sxs-lookup"><span data-stu-id="85bc1-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="85bc1-129">Para chamar o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método, seu assembly requer um nível de privilégio concedido pelo <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="85bc1-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="85bc1-130">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="85bc1-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="85bc1-131">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="85bc1-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="85bc1-132">O exemplo supõe que o formulário tem uma <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="85bc1-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
     <span data-ttu-id="85bc1-133">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="85bc1-133">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="85bc1-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85bc1-134">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="85bc1-135">Componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="85bc1-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
