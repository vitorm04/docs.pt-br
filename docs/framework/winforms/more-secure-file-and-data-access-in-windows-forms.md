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
ms.openlocfilehash: d5a9b08188e346fdea5b155149dee1ef8368c2a0
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696542"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Acesso mais seguro a arquivos e dados no Windows Forms
O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] usa permissões para ajudar a proteger recursos e dados. Onde seu aplicativo pode ler ou gravar dados depende das permissões concedidas ao aplicativo. Quando seu aplicativo é executado em um ambiente de confiança parcial, talvez você não tenha acesso aos seus dados ou talvez você precise alterar a maneira como você acessa os dados.  
  
 Quando você encontrar uma restrição de segurança, você tem duas opções: declarar a permissão (supondo que ela foi concedida ao seu aplicativo) ou use uma versão do recurso escrita para trabalhar em confiança parcial. As seções a seguir abordam como trabalhar com arquivos, o banco de dados e o acesso ao Registro de aplicativos que são executados em um ambiente parcialmente confiável.  
  
> [!NOTE]
>  Por padrão, as ferramentas que geram [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] implantações, padronizam essas distribuições para solicitar confiança total dos computadores em que são executadas. Se você decidir que deseja os benefícios de aumentar a segurança da execução em confiança parcial, você deve alterar esse padrão no Visual Studio ou em um do [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] ferramentas (Mage.exe ou MageUI.exe). Para obter mais informações sobre segurança dos Windows Forms e sobre como determinar o nível de confiança apropriado para seu aplicativo, consulte [Visão geral de Segurança nos Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Acesso a arquivos  
 O <xref:System.Security.Permissions.FileIOPermission> classe controla o acesso do arquivo e pasta no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Por padrão, o sistema de segurança não concede a <xref:System.Security.Permissions.FileIOPermission> para ambientes de confiança parcial, como a intranet local e zonas da Internet. No entanto, um aplicativo que requer acesso a arquivos ainda funcionará nesses ambientes se você modificar o design do seu aplicativo ou usa métodos diferentes para acessar arquivos. Por padrão, a zona da intranet local recebe o direito de ter o mesmo acesso a sites e o mesmo acesso a diretórios, para conectar-se novamente ao site de sua origem e ler seu diretório de instalação. Por padrão, a zona da Internet, é apenas o direito para se conectar novamente ao site de sua origem.  
  
### <a name="user-specified-files"></a>Arquivos especificados pelo usuário  
 Uma forma de lidar com não ter acesso a arquivos permissão é solicitar ao usuário para fornecer informações específicas do arquivo usando o <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> classe. Essa interação de usuário ajuda a fornecer alguma garantia de que o aplicativo não pode carregar arquivos particulares ou substituir arquivos importantes maliciosamente. O <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> e <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> métodos fornecem a leitura e gravação de acesso a arquivos, abrindo o fluxo de arquivos para o arquivo que o usuário especificado. Os métodos também ajudam a proteger o arquivo do usuário ocultando o caminho do arquivo.  
  
> [!NOTE]
>  Essas permissões são diferentes dependendo se o seu aplicativo estiver na zona da Internet ou zona da Intranet. Aplicativos da zona da Internet só podem usar o <xref:System.Windows.Forms.OpenFileDialog>, enquanto aplicativos de Intranet têm permissão de caixa de diálogo de arquivo irrestrita.  
  
 O <xref:System.Security.Permissions.FileDialogPermission> classe especifica o tipo de caixa de diálogo de arquivo que seu aplicativo pode usar. A tabela a seguir mostra o valor deve ter que usar cada <xref:System.Windows.Forms.FileDialog> classe.  
  
|Classe|Valor de acesso necessário|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  A permissão específica não é solicitada até que o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método é chamado.  
  
 Permissão para exibir uma caixa de diálogo não concede o aplicativo tenha acesso completo a todos os membros de <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, e <xref:System.Windows.Forms.SaveFileDialog> classes. Para as permissões exatas que são necessárias para chamar cada método, consulte o tópico de referência para o método na [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentação da biblioteca de classes.  
  
 O seguinte exemplo de código usa o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para abrir um arquivo especificado pelo usuário em um <xref:System.Windows.Forms.RichTextBox> controle. O exemplo requer <xref:System.Security.Permissions.FileDialogPermission> e os respectivos <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> valor de enumeração. O exemplo demonstra como manipular o <xref:System.Security.SecurityException> para determinar se o salvamento recurso deve ser desativado. Este exemplo requer que seu <xref:System.Windows.Forms.Form> tem uma <xref:System.Windows.Forms.Button> controle denominado `ButtonOpen`e uma <xref:System.Windows.Forms.RichTextBox> controle chamado `RtfBoxMain`.  
  
> [!NOTE]
>  A lógica de programação para o recurso de gravação não é mostrado no exemplo.  
  
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
>  No Visual c#, certifique-se de que você adicione código para permitir que o manipulador de eventos. Ao usar o código do exemplo anterior, o código a seguir mostra como habilitar o manipulador de eventos.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Outros arquivos  
 Às vezes, você precisará ler ou gravar em arquivos que o usuário não especifica, como quando você precisa salvar as configurações do aplicativo. Na intranet local e zonas da Internet, o aplicativo não terá permissão para armazenar dados em um arquivo local. No entanto, seu aplicativo poderá armazenar dados no armazenamento isolado. Armazenamento isolado é um compartimento de dados abstrato (não um local de armazenamento específico) que contém um ou mais arquivos de armazenamento isolados, chamados de armazenamentos, que contêm os locais reais dos diretórios nos quais os dados são armazenados. As permissões de acesso, como arquivos <xref:System.Security.Permissions.FileIOPermission> não são necessários; em vez disso, o <xref:System.Security.Permissions.IsolatedStoragePermission> classe controla as permissões para o armazenamento isolado. Por padrão, os aplicativos que são executados na intranet local e zonas da Internet podem armazenar dados usando armazenamento isolado; No entanto, configurações como cota de disco podem variar. Para obter mais informações sobre armazenamento isolado, consulte [Armazenamento Isolado](../../../docs/standard/io/isolated-storage.md).  
  
 O exemplo a seguir usa armazenamento isolado para gravar dados em um arquivo localizado em um repositório. O exemplo requer <xref:System.Security.Permissions.IsolatedStorageFilePermission> e o <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> valor de enumeração. O exemplo demonstra a leitura e gravação de certos valores de propriedades de <xref:System.Windows.Forms.Button> controle em um arquivo no armazenamento isolado. A função `Read` é chamada depois que o aplicativo é iniciado e a função `Write` é chamada antes do aplicativo terminar. O exemplo requer que o `Read` e `Write` existem funções como membros de uma <xref:System.Windows.Forms.Form> que contém um <xref:System.Windows.Forms.Button> controle chamado `MainButton`.  
  
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
  
## <a name="database-access"></a>Acesso ao banco de dados  
 As permissões necessárias para acessar um banco de dados variam de acordo com o provedor de banco de dados. No entanto, somente os aplicativos que estão executando com as permissões apropriadas podem acessar um banco de dados por meio de uma conexão de dados. Para obter mais informações sobre as permissões necessárias para acessar um banco de dados, consulte [Segurança de Acesso ao Código e ADO.NET](../../../docs/framework/data/adonet/code-access-security.md).  
  
 Se você não pode acessar um banco de dados diretamente, porque você deseja que o aplicativo seja executado em confiança parcial, você pode usar um serviço Web como um meio alternativo para acessar seus dados. Um serviço Web é um componente de software que pode ser acessado programaticamente através de uma rede. Com os serviços Web, aplicativos podem compartilhar dados entre zonas de grupos de códigos. Por padrão, a aplicativos na intranet local e zonas da Internet têm o direito de acessar seus sites de origem, que permite a chamar um serviço Web hospedado no mesmo servidor. Para obter mais informações, consulte [Serviços Web em ASP.NET AJAX](https://msdn.microsoft.com/library/8290e543-7eff-47a4-aace-681f3c07229b) ou [Windows Communication Foundation](https://msdn.microsoft.com/library/ms735119.aspx).  
  
## <a name="registry-access"></a>Acesso ao Registro  
 O <xref:System.Security.Permissions.RegistryPermission> classe controla o acesso ao registro do sistema operacional. Por padrão, somente aplicativos que estão sendo executados localmente podem acessar o Registro.  <xref:System.Security.Permissions.RegistryPermission> somente concede à aplicação o direito de tentar o acesso ao registro; ele não garante acesso terá êxito, porque o sistema operacional reforça ainda a segurança do registro.  
  
 Como você não pode acessar o Registro sob confiança parcial, você precisará encontrar outros métodos para armazenar seus dados. Quando você armazena configurações do aplicativo, use o armazenamento isolado em vez de no Registro. Armazenamento isolado também pode ser usado para armazenar outros arquivos específicos do aplicativo. Você também pode armazenar informações globais do aplicativo sobre o servidor ou site de origem, porque, por padrão, um aplicativo recebe o direito de acessar o seu site de origem.  
  
## <a name="see-also"></a>Consulte também  
 [Impressão mais segura no Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [Considerações adicionais sobre segurança nos Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Visão geral da segurança dos Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Segurança do Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)  
 [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
