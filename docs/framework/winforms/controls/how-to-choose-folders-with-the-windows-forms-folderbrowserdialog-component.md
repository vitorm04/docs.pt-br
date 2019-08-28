---
title: 'Como: Escolher pastas com o componente FolderBrowserDialog do Windows Forms'
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
ms.openlocfilehash: fc19ea466f535f783d3b0537a973ce41c223902d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046128"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Como: Escolher pastas com o componente FolderBrowserDialog do Windows Forms

Muitas vezes, dentro de aplicativos do Windows que você criou, será necessário solicitar que os usuários selecionem uma pasta e com mais frequência que eles salvem um conjunto de arquivos. O componente <xref:System.Windows.Forms.FolderBrowserDialog> Windows Forms permite que você realize essa tarefa facilmente.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Escolher pastas com o componente FolderBrowserDialog

1. Em um procedimento, verifique a <xref:System.Windows.Forms.FolderBrowserDialog> Propriedade do <xref:System.Windows.Forms.Form.DialogResult%2A> componente para ver como a caixa de diálogo foi fechada e <xref:System.Windows.Forms.FolderBrowserDialog> obter o <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> valor da Propriedade do componente.

2. Se você precisar definir a pasta superior que aparecerá dentro do modo de exibição de árvore da caixa de diálogo, defina a <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> Propriedade, que usa um membro <xref:System.Environment.SpecialFolder> da enumeração.

3. Além disso, você pode definir <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> a propriedade, que especifica a cadeia de caracteres de texto que aparece na parte superior da exibição de árvore de navegador de pasta.

    No exemplo a seguir, o <xref:System.Windows.Forms.FolderBrowserDialog> componente é usado para selecionar uma pasta, semelhante a quando você cria um projeto no Visual Studio e é solicitado a selecionar uma pasta na qual salvá-la. Neste exemplo, o nome da pasta é exibido em um <xref:System.Windows.Forms.TextBox> controle no formulário. É uma boa ideia posicionar o local em uma área editável, como um <xref:System.Windows.Forms.TextBox> controle, para que os usuários possam editar sua seleção em caso de erro ou outros problemas. Este exemplo pressupõe um formulário com um <xref:System.Windows.Forms.FolderBrowserDialog> componente e um <xref:System.Windows.Forms.TextBox> controle.

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
    > Para usar essa classe, seu assembly requer um nível <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> <xref:System.Security.Permissions.FileIOPermissionAccess> de privilégio concedido pela propriedade, que faz parte da enumeração. Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).

Para obter informações sobre como salvar arquivos, consulte [como: Salve os arquivos usando o componente](how-to-save-files-using-the-savefiledialog-component.md)SaveFileDialog.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Visão geral do componente FolderBrowserDialog (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [Componente FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
