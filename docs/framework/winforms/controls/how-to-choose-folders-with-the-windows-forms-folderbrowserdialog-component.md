---
title: Como escolher pastas com o componente FolderBrowserDialog dos Windows Forms
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
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0824fb70fa67628326af38ff7fb5e6c097a0378c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Como escolher pastas com o componente FolderBrowserDialog dos Windows Forms
Muitas vezes, dentro de aplicativos do Windows que você criou, será necessário solicitar que os usuários selecionem uma pasta e com mais frequência que eles salvem um conjunto de arquivos. Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> componente permite que você facilmente realizar essa tarefa.  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Escolher pastas com o componente FolderBrowserDialog  
  
1.  Em um procedimento, verifique o <xref:System.Windows.Forms.FolderBrowserDialog> do componente <xref:System.Windows.Forms.Form.DialogResult%2A> propriedade para ver como a caixa de diálogo foi fechada e obter o valor da <xref:System.Windows.Forms.FolderBrowserDialog> do componente <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriedade.  
  
2.  Se você precisa definir o nível mais alto pasta que será exibido na exibição de árvore da caixa de diálogo, defina o <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriedade, que usa um membro do <xref:System.Environment.SpecialFolder> enumeração.  
  
3.  Além disso, você pode definir o <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> propriedade, que especifica o texto da cadeia de caracteres que aparece na parte superior do modo de exibição de árvore do navegador de pasta.  
  
     No exemplo a seguir, o <xref:System.Windows.Forms.FolderBrowserDialog> componente é usado para selecionar uma pasta, semelhante a quando você cria um projeto no Visual Studio e é solicitado a selecionar uma pasta para salvá-lo no. Neste exemplo, o nome de pasta, em seguida, é exibido em um <xref:System.Windows.Forms.TextBox> controle no formulário. É aconselhável colocar o local em uma área editável, como um <xref:System.Windows.Forms.TextBox> controlar, de forma que os usuários podem editar sua seleção no caso de erro ou outros problemas. Este exemplo supõe que um formulário com um <xref:System.Windows.Forms.FolderBrowserDialog> componente e um <xref:System.Windows.Forms.TextBox> controle.  
  
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
    >  Para usar essa classe, seu assembly requer um nível de privilégio concedido pelo <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> propriedade, que é parte do <xref:System.Security.Permissions.FileIOPermissionAccess> enumeração. Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../docs/framework/misc/code-access-security-basics.md).  
  
 Para obter informações sobre como salvar arquivos, consulte [Como salvar arquivos usando o componente SaveFileDialog](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [Visão geral do componente FolderBrowserDialog (Windows Forms)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [Componente FolderBrowserDialog](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
