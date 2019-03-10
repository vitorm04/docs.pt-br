---
title: Acesso mais seguro a arquivos e dados no Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [Windows Forms], file access
- registry [Windows Forms]
- data access [Windows Forms]
- database access (Windows Forms security)
- data [Windows Forms], secure access
- file access [Windows Forms]
- security [Windows Forms], data access
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
ms.openlocfilehash: 60a9ffa8061f5bc576aa919aa742f1c5e6b07124
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724538"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a><span data-ttu-id="7a6cb-102">Acesso mais seguro a arquivos e dados no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a6cb-102">More Secure File and Data Access in Windows Forms</span></span>
<span data-ttu-id="7a6cb-103">O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] usa permissões para ajudar a proteger recursos e dados.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses permissions to help protect resources and data.</span></span> <span data-ttu-id="7a6cb-104">Onde seu aplicativo pode ler ou gravar dados depende das permissões concedidas ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-104">Where your application can read or write data depends on the permissions granted to the application.</span></span> <span data-ttu-id="7a6cb-105">Quando seu aplicativo é executado em um ambiente de confiança parcial, talvez você não tenha acesso aos seus dados ou talvez você precise alterar a maneira como você acessa os dados.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-105">When your application runs in a partial trust environment, you might not have access to your data or you might have to change the way you access the data.</span></span>  
  
 <span data-ttu-id="7a6cb-106">Quando você encontrar uma restrição de segurança, você tem duas opções: declarar a permissão (supondo que ela foi concedida ao seu aplicativo) ou use uma versão do recurso escrita para trabalhar em confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-106">When you encounter a security restriction, you have two options: assert the permission (assuming it has been granted to your application), or use a version of the feature written to work in partial trust.</span></span> <span data-ttu-id="7a6cb-107">As seções a seguir abordam como trabalhar com arquivos, o banco de dados e o acesso ao Registro de aplicativos que são executados em um ambiente parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-107">The following sections discuss how to work with file, database, and registry access from applications that are running in a partial trust environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a6cb-108">Por padrão, as ferramentas que geram [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] implantações, padronizam essas distribuições para solicitar confiança total dos computadores em que são executadas.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-108">By default, tools that generate [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployments default these deployments to requesting Full Trust from the computers on which they run.</span></span> <span data-ttu-id="7a6cb-109">Se você decidir que deseja os benefícios de aumentar a segurança da execução em confiança parcial, você deve alterar esse padrão no Visual Studio ou em um do [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] ferramentas (Mage.exe ou MageUI.exe).</span><span class="sxs-lookup"><span data-stu-id="7a6cb-109">If you decide you want the added security benefits of running in partial trust, you must change this default in either Visual Studio or one of the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] tools (Mage.exe or MageUI.exe).</span></span> <span data-ttu-id="7a6cb-110">Para obter mais informações sobre segurança dos Windows Forms e sobre como determinar o nível de confiança apropriado para seu aplicativo, consulte [Visão geral de Segurança nos Windows Forms](security-in-windows-forms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7a6cb-110">For more information about Windows Forms security, and on how to determine the appropriate trust level for your application, see [Security in Windows Forms Overview](security-in-windows-forms-overview.md).</span></span>  
  
## <a name="file-access"></a><span data-ttu-id="7a6cb-111">Acesso a arquivos</span><span class="sxs-lookup"><span data-stu-id="7a6cb-111">File Access</span></span>  
 <span data-ttu-id="7a6cb-112">O <xref:System.Security.Permissions.FileIOPermission> classe controla o acesso do arquivo e pasta no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a6cb-112">The <xref:System.Security.Permissions.FileIOPermission> class controls file and folder access in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="7a6cb-113">Por padrão, o sistema de segurança não concede a <xref:System.Security.Permissions.FileIOPermission> para ambientes de confiança parcial, como a intranet local e zonas da Internet.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-113">By default, the security system does not grant the <xref:System.Security.Permissions.FileIOPermission> to partial trust environments such as the local intranet and Internet zones.</span></span> <span data-ttu-id="7a6cb-114">No entanto, um aplicativo que requer acesso a arquivos ainda funcionará nesses ambientes se você modificar o design do seu aplicativo ou usa métodos diferentes para acessar arquivos.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-114">However, an application that requires file access can still function in these environments if you modify the design of your application or use different methods to access files.</span></span> <span data-ttu-id="7a6cb-115">Por padrão, a zona da intranet local recebe o direito de ter o mesmo acesso a sites e o mesmo acesso a diretórios, para conectar-se novamente ao site de sua origem e ler seu diretório de instalação.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-115">By default, the local intranet zone is granted the right to have same site access and same directory access, to connect back to the site of its origin, and to read from its installation directory.</span></span> <span data-ttu-id="7a6cb-116">Por padrão, a zona da Internet, é apenas o direito para se conectar novamente ao site de sua origem.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-116">By default, the Internet zone, is only granted the right to connect back to the site of its origin.</span></span>  
  
### <a name="user-specified-files"></a><span data-ttu-id="7a6cb-117">Arquivos especificados pelo usuário</span><span class="sxs-lookup"><span data-stu-id="7a6cb-117">User-Specified Files</span></span>  
 <span data-ttu-id="7a6cb-118">Uma forma de lidar com não ter acesso a arquivos permissão é solicitar ao usuário para fornecer informações específicas do arquivo usando o <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> classe.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-118">One way to deal with not having file access permission is to prompt the user to provide specific file information by using the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> class.</span></span> <span data-ttu-id="7a6cb-119">Essa interação de usuário ajuda a fornecer alguma garantia de que o aplicativo não pode carregar arquivos particulares ou substituir arquivos importantes maliciosamente.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-119">This user interaction helps provide some assurance that the application cannot maliciously load private files or overwrite important files.</span></span> <span data-ttu-id="7a6cb-120">O <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> e <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> métodos fornecem a leitura e gravação de acesso a arquivos, abrindo o fluxo de arquivos para o arquivo que o usuário especificado.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-120">The <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> and <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> methods provide read and write file access by opening the file stream for the file that the user specified.</span></span> <span data-ttu-id="7a6cb-121">Os métodos também ajudam a proteger o arquivo do usuário ocultando o caminho do arquivo.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-121">The methods also help protect the user's file by obscuring the file's path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a6cb-122">Essas permissões são diferentes dependendo se o seu aplicativo estiver na zona da Internet ou zona da Intranet.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-122">These permissions differ depending on whether your application is in the Internet zone or Intranet zone.</span></span> <span data-ttu-id="7a6cb-123">Aplicativos da zona da Internet só podem usar o <xref:System.Windows.Forms.OpenFileDialog>, enquanto aplicativos de Intranet têm permissão de caixa de diálogo de arquivo irrestrita.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-123">Internet zone applications can only use the <xref:System.Windows.Forms.OpenFileDialog>, whereas Intranet applications have unrestricted file dialog permission.</span></span>  
  
 <span data-ttu-id="7a6cb-124">O <xref:System.Security.Permissions.FileDialogPermission> classe especifica o tipo de caixa de diálogo de arquivo que seu aplicativo pode usar.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-124">The <xref:System.Security.Permissions.FileDialogPermission> class specifies what type of file dialog box your application can use.</span></span> <span data-ttu-id="7a6cb-125">A tabela a seguir mostra o valor deve ter que usar cada <xref:System.Windows.Forms.FileDialog> classe.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-125">The following table shows the value you must have to use each <xref:System.Windows.Forms.FileDialog> class.</span></span>  
  
|<span data-ttu-id="7a6cb-126">Classe</span><span class="sxs-lookup"><span data-stu-id="7a6cb-126">Class</span></span>|<span data-ttu-id="7a6cb-127">Valor de acesso necessário</span><span class="sxs-lookup"><span data-stu-id="7a6cb-127">Required access value</span></span>|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  <span data-ttu-id="7a6cb-128">A permissão específica não é solicitada até que o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método é chamado.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-128">The specific permission is not requested until the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is actually called.</span></span>  
  
 <span data-ttu-id="7a6cb-129">Permissão para exibir uma caixa de diálogo não concede o aplicativo tenha acesso completo a todos os membros de <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, e <xref:System.Windows.Forms.SaveFileDialog> classes.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-129">Permission to display a file dialog box does not grant your application full access to all members of the <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, and <xref:System.Windows.Forms.SaveFileDialog> classes.</span></span> <span data-ttu-id="7a6cb-130">Para as permissões exatas que são necessárias para chamar cada método, consulte o tópico de referência para o método na [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentação da biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-130">For the exact permissions that are required to call each method, see the reference topic for that method in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library documentation.</span></span>  
  
 <span data-ttu-id="7a6cb-131">O seguinte exemplo de código usa o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para abrir um arquivo especificado pelo usuário em um <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-131">The following code example uses the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open a user-specified file into a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="7a6cb-132">O exemplo requer <xref:System.Security.Permissions.FileDialogPermission> e os respectivos <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> valor de enumeração.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-132">The example requires <xref:System.Security.Permissions.FileDialogPermission> and the associated <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> enumeration value.</span></span> <span data-ttu-id="7a6cb-133">O exemplo demonstra como manipular o <xref:System.Security.SecurityException> para determinar se o salvamento recurso deve ser desativado.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-133">The example demonstrates how to handle the <xref:System.Security.SecurityException> to determine whether the save feature should be disabled.</span></span> <span data-ttu-id="7a6cb-134">Este exemplo requer que seu <xref:System.Windows.Forms.Form> tem uma <xref:System.Windows.Forms.Button> controle denominado `ButtonOpen`e uma <xref:System.Windows.Forms.RichTextBox> controle chamado `RtfBoxMain`.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-134">This example requires that your <xref:System.Windows.Forms.Form> has a <xref:System.Windows.Forms.Button> control named `ButtonOpen`, and a <xref:System.Windows.Forms.RichTextBox> control named `RtfBoxMain`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a6cb-135">A lógica de programação para o recurso de gravação não é mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-135">The programming logic for the save feature is not shown in the example.</span></span>  
  
```vb  
Private Sub ButtonOpen_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles ButtonOpen.Click   
  
    Dim editingFileName as String = ""  
    Dim saveAllowed As Boolean = True  
  
    ' Displays the OpenFileDialog.  
    If (OpenFileDialog1.ShowDialog() = DialogResult.OK) Then  
        Dim userStream as System.IO.Stream  
        Try   
            ' Opens the file stream for the file selected by the user.  
            userStream =OpenFileDialog1.OpenFile()   
            Me.RtfBoxMain.LoadFile(userStream, _  
                RichTextBoxStreamType.PlainText)  
        Finally  
            userStream.Close()  
        End Try  
  
        ' Tries to get the file name selected by the user.  
        ' Failure means that the application does not have  
        ' unrestricted permission to the file.  
        Try   
            editingFileName = OpenFileDialog1.FileName  
        Catch ex As Exception  
            If TypeOf ex Is System.Security.SecurityException Then   
                ' The application does not have unrestricted permission   
                ' to the file so the save feature will be disabled.  
                saveAllowed = False   
            Else   
                Throw ex  
            End If  
        End Try  
    End If  
End Sub  
```  
  
```csharp  
private void ButtonOpen_Click(object sender, System.EventArgs e)   
{  
    String editingFileName = "";  
    Boolean saveAllowed = true;  
  
    // Displays the OpenFileDialog.  
    if (openFileDialog1.ShowDialog() == DialogResult.OK)   
    {  
        // Opens the file stream for the file selected by the user.  
        using (System.IO.Stream userStream = openFileDialog1.OpenFile())   
        {  
            this.RtfBoxMain.LoadFile(userStream,  
                RichTextBoxStreamType.PlainText);  
            userStream.Close();  
        }  
  
        // Tries to get the file name selected by the user.  
        // Failure means that the application does not have  
        // unrestricted permission to the file.  
        try   
        {  
            editingFileName = openFileDialog1.FileName;  
        }   
        catch (Exception ex)   
        {  
            if (ex is System.Security.SecurityException)   
            {  
                // The application does not have unrestricted permission   
                // to the file so the save feature will be disabled.  
                saveAllowed = false;   
            }   
            else   
            {  
                throw ex;  
            }  
        }  
    }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="7a6cb-136">No Visual c#, certifique-se de que você adicione código para permitir que o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-136">In Visual C#, ensure that you add code to enable the event handler.</span></span> <span data-ttu-id="7a6cb-137">Ao usar o código do exemplo anterior, o código a seguir mostra como habilitar o manipulador de eventos.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span><span class="sxs-lookup"><span data-stu-id="7a6cb-137">By using the code from the previous example, the following code shows how to enable the event handler.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span></span>  
  
### <a name="other-files"></a><span data-ttu-id="7a6cb-138">Outros arquivos</span><span class="sxs-lookup"><span data-stu-id="7a6cb-138">Other Files</span></span>  
 <span data-ttu-id="7a6cb-139">Às vezes, você precisará ler ou gravar em arquivos que o usuário não especifica, como quando você precisa salvar as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-139">Sometimes you will need to read or write to files that the user does not specify, such as when you must persist application settings.</span></span> <span data-ttu-id="7a6cb-140">Na intranet local e zonas da Internet, o aplicativo não terá permissão para armazenar dados em um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-140">In the local intranet and Internet zones, your application will not have permission to store data in a local file.</span></span> <span data-ttu-id="7a6cb-141">No entanto, seu aplicativo poderá armazenar dados no armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-141">However, your application will be able to store data in isolated storage.</span></span> <span data-ttu-id="7a6cb-142">Armazenamento isolado é um compartimento de dados abstrato (não um local de armazenamento específico) que contém um ou mais arquivos de armazenamento isolados, chamados de armazenamentos, que contêm os locais reais dos diretórios nos quais os dados são armazenados.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-142">Isolated storage is an abstract data compartment (not a specific storage location) that contains one or more isolated storage files, called stores, that contain the actual directory locations where data is stored.</span></span> <span data-ttu-id="7a6cb-143">As permissões de acesso, como arquivos <xref:System.Security.Permissions.FileIOPermission> não são necessários; em vez disso, o <xref:System.Security.Permissions.IsolatedStoragePermission> classe controla as permissões para o armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-143">File access permissions like <xref:System.Security.Permissions.FileIOPermission> are not required; instead, the <xref:System.Security.Permissions.IsolatedStoragePermission> class controls the permissions for isolated storage.</span></span> <span data-ttu-id="7a6cb-144">Por padrão, os aplicativos que são executados na intranet local e zonas da Internet podem armazenar dados usando armazenamento isolado; No entanto, configurações como cota de disco podem variar.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-144">By default, applications that are running in the local intranet and Internet zones can store data using isolated storage; however, settings like disk quota can vary.</span></span> <span data-ttu-id="7a6cb-145">Para obter mais informações sobre armazenamento isolado, consulte [Armazenamento Isolado](../../standard/io/isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="7a6cb-145">For more information about isolated storage, see [Isolated Storage](../../standard/io/isolated-storage.md).</span></span>  
  
 <span data-ttu-id="7a6cb-146">O exemplo a seguir usa armazenamento isolado para gravar dados em um arquivo localizado em um repositório.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-146">The following example uses isolated storage to write data to a file located in a store.</span></span> <span data-ttu-id="7a6cb-147">O exemplo requer <xref:System.Security.Permissions.IsolatedStorageFilePermission> e o <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> valor de enumeração.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-147">The example requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> and the <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> enumeration value.</span></span> <span data-ttu-id="7a6cb-148">O exemplo demonstra a leitura e gravação de certos valores de propriedades de <xref:System.Windows.Forms.Button> controle em um arquivo no armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-148">The example demonstrates reading and writing certain property values of the <xref:System.Windows.Forms.Button> control to a file in isolated storage.</span></span> <span data-ttu-id="7a6cb-149">A função `Read` é chamada depois que o aplicativo é iniciado e a função `Write` é chamada antes do aplicativo terminar.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-149">The `Read` function would be called after the application starts and the `Write` function would be called before the application ends.</span></span> <span data-ttu-id="7a6cb-150">O exemplo requer que o `Read` e `Write` existem funções como membros de uma <xref:System.Windows.Forms.Form> que contém um <xref:System.Windows.Forms.Button> controle chamado `MainButton`.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-150">The example requires that the `Read` and `Write` functions exist as members of a <xref:System.Windows.Forms.Form> that contains a <xref:System.Windows.Forms.Button> control named `MainButton`.</span></span>  
  
```vb  
' Reads the button options from the isolated storage. Uses Default values   
' for the button if the options file does not exist.  
Public Sub Read()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try  
        ' Checks to see if the options.txt file exists.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
  
            ' Opens the file because it exists.  
            Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
                 (filename, IO.FileMode.Open,isoStore)  
            Dim reader as System.IO.StreamReader  
            Try   
                reader = new System.IO.StreamReader(isos)  
  
                ' Reads the values stored.  
                Dim converter As System.ComponentModel.TypeConverter  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Color))  
  
                Me.MainButton.BackColor = _   
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
                me.MainButton.ForeColor = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Font))  
                me.MainButton.Font = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Font)  
  
            Catch ex As Exception  
                Debug.WriteLine("Cannot read options " + _  
                    ex.ToString())  
            Finally  
                reader.Close()  
            End Try  
        End If  
  
    Catch ex As Exception  
        Debug.WriteLine("Cannot read options " + ex.ToString())  
    End Try  
End Sub  
  
' Writes the button options to the isolated storage.  
Public Sub Write()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try   
        ' Checks if the file exists, and if it does, tries to delete it.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
            isoStore.DeleteFile(filename)  
        End If  
    Catch ex As Exception  
        Debug.WriteLine("Cannot delete file " + ex.ToString())  
    End Try  
  
    ' Creates the options.txt file and writes the button options to it.  
    Dim writer as System.IO.StreamWriter  
    Try   
        Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
             (filename, IO.FileMode.CreateNew, isoStore)  
  
        writer = New System.IO.StreamWriter(isos)  
        Dim converter As System.ComponentModel.TypeConverter  
  
        converter = System.ComponentModel.TypeDescriptor.GetConverter _   
           (GetType(Color))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.BackColor))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.ForeColor))  
  
        converter = System.ComponentModel TypeDescriptor.GetConverter _   
           (GetType(Font))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.Font))  
  
    Catch ex as Exception  
        Debug.WriteLine("Cannot write options " + ex.ToString())  
  
    Finally  
        writer.Close()  
    End Try  
End Sub  
```  
  
```csharp  
// Reads the button options from the isolated storage. Uses default values   
// for the button if the options file does not exist.  
public void Read()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try  
    {  
        // Checks to see if the options.txt file exists.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            // Opens the file because it exists.  
            System.IO.IsolatedStorage.IsolatedStorageFileStream isos =   
                new System.IO.IsolatedStorage.IsolatedStorageFileStream  
                    (filename, System.IO.FileMode.Open,isoStore);  
            System.IO.StreamReader reader = null;  
            try   
            {  
                reader = new System.IO.StreamReader(isos);  
  
                // Reads the values stored.  
                TypeConverter converter ;  
                converter = TypeDescriptor.GetConverter(typeof(Color));  
  
                this.MainButton.BackColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
                this.MainButton.ForeColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
  
                converter = TypeDescriptor.GetConverter(typeof(Font));  
                this.MainButton.Font =   
                  (Font)(converter.ConvertFromString(reader.ReadLine()));  
            }  
            catch (Exception ex)  
            {   
                System.Diagnostics.Debug.WriteLine  
                     ("Cannot read options " + ex.ToString());  
            }  
            finally  
            {  
                reader.Close();  
            }  
        }  
    }   
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot read options " + ex.ToString());  
    }  
}  
  
// Writes the button options to the isolated storage.  
public void Write()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try   
    {  
        // Checks if the file exists and, if it does, tries to delete it.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            isoStore.DeleteFile(filename);  
        }  
    }  
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot delete file " + ex.ToString());  
    }  
  
    // Creates the options file and writes the button options to it.  
    System.IO.StreamWriter writer = null;  
    try   
    {  
        System.IO.IsolatedStorage.IsolatedStorageFileStream isos = new   
            System.IO.IsolatedStorage.IsolatedStorageFileStream(filename,   
            System.IO.FileMode.CreateNew,isoStore);  
  
        writer = new System.IO.StreamWriter(isos);  
        TypeConverter converter ;  
  
        converter = TypeDescriptor.GetConverter(typeof(Color));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.BackColor));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.ForeColor));  
  
        converter = TypeDescriptor.GetConverter(typeof(Font));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.Font));  
  
    }  
    catch (Exception ex)  
    {   
        System.Diagnostics.Debug.WriteLine  
           ("Cannot write options " + ex.ToString());  
    }  
    finally  
    {  
        writer.Close();  
    }  
}  
```  
  
## <a name="database-access"></a><span data-ttu-id="7a6cb-151">Acesso ao banco de dados</span><span class="sxs-lookup"><span data-stu-id="7a6cb-151">Database Access</span></span>  
 <span data-ttu-id="7a6cb-152">As permissões necessárias para acessar um banco de dados variam de acordo com o provedor de banco de dados. No entanto, somente os aplicativos que estão executando com as permissões apropriadas podem acessar um banco de dados por meio de uma conexão de dados.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-152">The permissions required to access a database vary based on the database provider; however, only applications that are running with the appropriate permissions can access a database through a data connection.</span></span> <span data-ttu-id="7a6cb-153">Para obter mais informações sobre as permissões necessárias para acessar um banco de dados, consulte [Segurança de Acesso ao Código e ADO.NET](../data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="7a6cb-153">For more information about the permissions that are required to access a database, see [Code Access Security and ADO.NET](../data/adonet/code-access-security.md).</span></span>  
  
 <span data-ttu-id="7a6cb-154">Se você não pode acessar um banco de dados diretamente, porque você deseja que o aplicativo seja executado em confiança parcial, você pode usar um serviço Web como um meio alternativo para acessar seus dados.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-154">If you cannot directly access a database because you want your application to run in partial trust, you can use a Web service as an alternative means to access your data.</span></span> <span data-ttu-id="7a6cb-155">Um serviço Web é um componente de software que pode ser acessado programaticamente através de uma rede.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-155">A Web service is a piece of software that can be programmatically accessed over a network.</span></span> <span data-ttu-id="7a6cb-156">Com os serviços Web, aplicativos podem compartilhar dados entre zonas de grupos de códigos.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-156">With Web services, applications can share data across code group zones.</span></span> <span data-ttu-id="7a6cb-157">Por padrão, a aplicativos na intranet local e zonas da Internet têm o direito de acessar seus sites de origem, que permite a chamar um serviço Web hospedado no mesmo servidor.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-157">By default, applications in the local intranet and Internet zones are granted the right to access their sites of origin, which enables them to call a Web service hosted on the same server.</span></span> <span data-ttu-id="7a6cb-158">Para obter mais informações, consulte [Serviços Web em ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) ou [Windows Communication Foundation](../wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="7a6cb-158">For more information see [Web Services in ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) or [Windows Communication Foundation](../wcf/index.md).</span></span>  
  
## <a name="registry-access"></a><span data-ttu-id="7a6cb-159">Acesso ao Registro</span><span class="sxs-lookup"><span data-stu-id="7a6cb-159">Registry Access</span></span>  
 <span data-ttu-id="7a6cb-160">O <xref:System.Security.Permissions.RegistryPermission> classe controla o acesso ao registro do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-160">The <xref:System.Security.Permissions.RegistryPermission> class controls access to the operating system registry.</span></span> <span data-ttu-id="7a6cb-161">Por padrão, somente aplicativos que estão sendo executados localmente podem acessar o Registro.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-161">By default, only applications that are running locally can access the registry.</span></span>  <span data-ttu-id="7a6cb-162"><xref:System.Security.Permissions.RegistryPermission> somente concede à aplicação o direito de tentar o acesso ao registro; ele não garante acesso terá êxito, porque o sistema operacional reforça ainda a segurança do registro.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-162"><xref:System.Security.Permissions.RegistryPermission> only grants an application the right to try registry access; it does not guarantee access will succeed, because the operating system still enforces security on the registry.</span></span>  
  
 <span data-ttu-id="7a6cb-163">Como você não pode acessar o Registro sob confiança parcial, você precisará encontrar outros métodos para armazenar seus dados.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-163">Because you cannot access the registry under partial trust, you may need to find other methods of storing your data.</span></span> <span data-ttu-id="7a6cb-164">Quando você armazena configurações do aplicativo, use o armazenamento isolado em vez de no Registro.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-164">When you store application settings, use isolated storage instead of the registry.</span></span> <span data-ttu-id="7a6cb-165">Armazenamento isolado também pode ser usado para armazenar outros arquivos específicos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-165">Isolated storage can also be used to store other application-specific files.</span></span> <span data-ttu-id="7a6cb-166">Você também pode armazenar informações globais do aplicativo sobre o servidor ou site de origem, porque, por padrão, um aplicativo recebe o direito de acessar o seu site de origem.</span><span class="sxs-lookup"><span data-stu-id="7a6cb-166">You can also store global application information about the server or site of origin, because by default an application is granted the right to access the site of its origin.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6cb-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a6cb-167">See also</span></span>
- [<span data-ttu-id="7a6cb-168">Impressão mais segura no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a6cb-168">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)
- [<span data-ttu-id="7a6cb-169">Considerações adicionais sobre segurança nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a6cb-169">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="7a6cb-170">Visão geral da segurança dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a6cb-170">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="7a6cb-171">Segurança do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a6cb-171">Windows Forms Security</span></span>](windows-forms-security.md)
- [<span data-ttu-id="7a6cb-172">Mage.exe (Manifest Generation and Editing Tool)</span><span class="sxs-lookup"><span data-stu-id="7a6cb-172">Mage.exe (Manifest Generation and Editing Tool)</span></span>](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [<span data-ttu-id="7a6cb-173">MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)</span><span class="sxs-lookup"><span data-stu-id="7a6cb-173">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
