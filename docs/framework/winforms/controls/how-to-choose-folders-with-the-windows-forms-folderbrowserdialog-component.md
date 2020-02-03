---
title: Escolher pastas com o componente FolderBrowserDialog
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
ms.openlocfilehash: 313388442101f341cfed366143f3c9669fb45cbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742235"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Como escolher pastas com o componente FolderBrowserDialog dos Windows Forms

Muitas vezes, dentro de aplicativos do Windows que você criou, será necessário solicitar que os usuários selecionem uma pasta e com mais frequência que eles salvem um conjunto de arquivos. O componente Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> permite que você realize essa tarefa facilmente.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Escolher pastas com o componente FolderBrowserDialog

1. Em um procedimento, verifique a propriedade <xref:System.Windows.Forms.Form.DialogResult%2A> do componente de <xref:System.Windows.Forms.FolderBrowserDialog> para ver como a caixa de diálogo foi fechada e obter o valor da propriedade <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> do componente de <xref:System.Windows.Forms.FolderBrowserDialog>.

2. Se você precisar definir a pasta superior que aparecerá dentro do modo de exibição de árvore da caixa de diálogo, defina a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, que usa um membro da enumeração <xref:System.Environment.SpecialFolder>.

3. Além disso, você pode definir a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>, que especifica a cadeia de texto que aparece na parte superior da exibição de árvore de navegador de pasta.

    No exemplo a seguir, o componente <xref:System.Windows.Forms.FolderBrowserDialog> é usado para selecionar uma pasta, semelhante a quando você cria um projeto no Visual Studio e é solicitado a selecionar uma pasta na qual salvá-la. Neste exemplo, o nome da pasta é exibido em um controle <xref:System.Windows.Forms.TextBox> no formulário. É uma boa ideia posicionar o local em uma área editável, como um controle de <xref:System.Windows.Forms.TextBox>, para que os usuários possam editar sua seleção em caso de erro ou outros problemas. Este exemplo pressupõe um formulário com um componente <xref:System.Windows.Forms.FolderBrowserDialog> e um controle <xref:System.Windows.Forms.TextBox>.

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
    > Para usar essa classe, seu assembly requer um nível de privilégio concedido pela propriedade <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>, que faz parte da enumeração <xref:System.Security.Permissions.FileIOPermissionAccess>. Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).

Para obter informações sobre como salvar arquivos, consulte [Como salvar arquivos usando o componente SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Visão geral do componente FolderBrowserDialog (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [Componente FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
