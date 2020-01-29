---
title: Carregar arquivos no controle RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: c31e004ea4cd0821b5f18f0ab0fe2708e6ac4b59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736290"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Como carregar arquivos no controle RichTextBox dos Windows Forms

O controle de <xref:System.Windows.Forms.RichTextBox> de Windows Forms pode exibir um arquivo de texto sem formatação de texto sem formatação, Unicode ou RTF (Rich-Text-Format). Para fazer isso, chame o método <xref:System.Windows.Forms.RichTextBox.LoadFile%2A>. Você também pode usar o método <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> para carregar dados de um fluxo. Para obter mais informações, consulte <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-load-a-file-into-the-richtextbox-control"></a>Para carregar um Arquivo no controle RichTextBox

1. Determine o caminho do arquivo a ser aberto usando o componente <xref:System.Windows.Forms.OpenFileDialog>. Para obter uma visão geral, consulte [Visão geral do componente OpenFileDialog](openfiledialog-component-overview-windows-forms.md).

2. Chame o método <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> do controle <xref:System.Windows.Forms.RichTextBox>, especificando o arquivo a ser carregado e, opcionalmente, um tipo de arquivo. No exemplo a seguir, o arquivo a ser carregado é obtido da propriedade <xref:System.Windows.Forms.FileDialog.FileName%2A> do componente de <xref:System.Windows.Forms.OpenFileDialog>. Se você chamar o método com um nome de arquivo como seu único argumento, o tipo de arquivo será considerado como RTF. Para especificar outro tipo de arquivo, chame o método com um valor da enumeração <xref:System.Windows.Forms.RichTextBoxStreamType> como seu segundo argumento.

    No exemplo a seguir, o componente <xref:System.Windows.Forms.OpenFileDialog> é mostrado quando um botão é clicado. O arquivo selecionado é então aberto e exibido no controle de <xref:System.Windows.Forms.RichTextBox>. Este exemplo supõe que um formulário tem um botão, `btnOpenFile`.

    ```vb
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _
       ByVal e As System.EventArgs) Handles btnOpenFile.Click
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _
              RichTextBoxStreamType.RichText)
          End If
    End Sub
    ```

    ```csharp
    private void btnOpenFile_Click(object sender, System.EventArgs e)
    {
       if(openFileDialog1.ShowDialog() == DialogResult.OK)
       {
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);
       }
    }
    ```

    ```cpp
    private:
       void btnOpenFile_Click(System::Object ^  sender,
          System::EventArgs ^  e)
       {
          if(openFileDialog1->ShowDialog() == DialogResult::OK)
          {
             richTextBox1->LoadFile(openFileDialog1->FileName,
                RichTextBoxStreamType::RichText);
          }
       }
    ```

    (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > Para executar esse processo, seu assembly pode exigir um nível de privilégio concedido pela classe <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>. Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
