---
title: 'Como: Escolher pastas com o componente do Windows Forms FolderBrowserDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: ea5fdc9708d8e896eb66fa42f64cac672baff08b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724547"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Como: Escolher pastas com o componente do Windows Forms FolderBrowserDialog
Muitas vezes, dentro de aplicativos do Windows que você criou, será necessário solicitar que os usuários selecionem uma pasta e com mais frequência que eles salvem um conjunto de arquivos. Os formulários do Windows <xref:System.Windows.Forms.FolderBrowserDialog> componente permite que você facilmente realizar essa tarefa.  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Escolher pastas com o componente FolderBrowserDialog  
  
1.  Em um procedimento, verifique as <xref:System.Windows.Forms.FolderBrowserDialog> do componente <xref:System.Windows.Forms.Form.DialogResult%2A> propriedade para ver como a caixa de diálogo foi fechada e obter o valor da <xref:System.Windows.Forms.FolderBrowserDialog> do componente <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriedade.  
  
2.  Se você precisar de pasta de conjunto o mais alto que será exibido dentro da exibição de árvore da caixa de diálogo, defina as <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriedade, que usa um membro do <xref:System.Environment.SpecialFolder> enumeração.  
  
3.  Além disso, você pode definir o <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> propriedade, que especifica o texto da cadeia de caracteres que aparece na parte superior do modo de exibição de árvore do navegador de pasta.  
  
     No exemplo a seguir, o <xref:System.Windows.Forms.FolderBrowserDialog> componente é usado para selecionar uma pasta, semelhante a quando você cria um projeto no Visual Studio e será solicitado a selecionar uma pasta para salvá-lo no. Neste exemplo, o nome da pasta é exibido em um <xref:System.Windows.Forms.TextBox> controle no formulário. É uma boa ideia colocar o local em uma área editável, como um <xref:System.Windows.Forms.TextBox> controle, para que os usuários podem editar a seleção em caso de erro ou outros problemas. Este exemplo pressupõe um formulário com um <xref:System.Windows.Forms.FolderBrowserDialog> componente e um <xref:System.Windows.Forms.TextBox> controle.  
  
    ```vb  
    Public Sub ChooseFolder()  
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then  
            TextBox1.Text = FolderBrowserDialog1.SelectedPath  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    public void ChooseFolder()  
    {  
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)   
        {  
            textBox1.Text = folderBrowserDialog1.SelectedPath;  
        }  
    }  
    ```  
  
    ```cpp  
    public:  
       void ChooseFolder()  
       {  
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Text = folderBrowserDialog1->SelectedPath;  
          }  
       }  
    ```  
  
    > [!IMPORTANT]
    >  Para usar essa classe, seu assembly requer um nível de privilégio concedido pela <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> propriedade, que é parte do <xref:System.Security.Permissions.FileIOPermissionAccess> enumeração. Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).  
  
 Para obter informações sobre como salvar arquivos, consulte [como: Salvar arquivos usando o componente SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Visão geral do componente FolderBrowserDialog (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [Componente FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
