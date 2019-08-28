---
title: 'Como: Salvar arquivos usando o componente SaveFileDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
ms.openlocfilehash: 7a3a7d0b12a83b756eb2790a94a95580576a2c32
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046271"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>Como: Salvar arquivos usando o componente SaveFileDialog

O <xref:System.Windows.Forms.SaveFileDialog> componente permite que os usuários procurem o sistema de arquivos e selecionem os arquivos a serem salvos. A caixa de diálogo retorna o caminho e o nome do arquivo que o usuário selecionou na caixa de diálogo. No entanto, você deve escrever o código para efetivamente gravar os arquivos no disco.

### <a name="to-save-a-file-using-the-savefiledialog-component"></a>Salvar arquivos usando o componente SaveFileDialog

- Exiba a caixa de diálogo **Salvar Arquivo** e chame um método para salvar o arquivo selecionado pelo usuário.

  Use o <xref:System.Windows.Forms.SaveFileDialog> método do <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> componente para salvar o arquivo. Esse método fornece um <xref:System.IO.Stream> objeto no qual você pode gravar.

  O exemplo a seguir usa <xref:System.Windows.Forms.DialogResult> a propriedade para obter o nome do arquivo e o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para salvar o arquivo. O <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> método fornece um fluxo no qual gravar o arquivo.

  No exemplo a seguir, há um <xref:System.Windows.Forms.Button> controle com uma imagem atribuída a ele. Quando você clica no botão, um <xref:System.Windows.Forms.SaveFileDialog> componente é instanciado com um filtro que permite arquivos do tipo. gif,. jpeg e. bmp. Se um arquivo desse tipo for selecionado na caixa de diálogo Salvar Arquivo, a imagem do botão será salva.

  > [!IMPORTANT]
  > Para obter ou definir a <xref:System.Windows.Forms.FileDialog.FileName%2A> Propriedade, seu assembly requer um nível de privilégio concedido <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> pela classe. Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).

  O exemplo supõe que seu formulário tenha <xref:System.Windows.Forms.Button> um controle com <xref:System.Windows.Forms.ButtonBase.Image%2A> sua propriedade definida como um arquivo de Type. gif,. jpeg ou. bmp.

  > [!NOTE]
  > A <xref:System.Windows.Forms.FileDialog> propriedade da <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> classe (que, devido à herança <xref:System.Windows.Forms.SaveFileDialog> , faz parte da classe) usa um índice baseado em um. Isso será importante se você estiver escrevendo código para salvar dados em um formato específico (por exemplo, salvar um arquivo como texto sem formatação em vez de formato binário). Essa propriedade é apresentada no exemplo abaixo.

  ```vb
  Private Sub Button2_Click(ByVal sender As System.Object, _
  ByVal e As System.EventArgs) Handles Button2.Click
      ' Displays a SaveFileDialog so the user can save the Image
      ' assigned to Button2.
      Dim saveFileDialog1 As New SaveFileDialog()
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"
      saveFileDialog1.Title = "Save an Image File"
      saveFileDialog1.ShowDialog()

      ' If the file name is not an empty string open it for saving.
      If saveFileDialog1.FileName <> "" Then
        ' Saves the Image via a FileStream created by the OpenFile method.
        Dim fs As System.IO.FileStream = Ctype _
            (saveFileDialog1.OpenFile(), System.IO.FileStream)
        ' Saves the Image in the appropriate ImageFormat based upon the
        ' file type selected in the dialog box.
        ' NOTE that the FilterIndex property is one-based.
        Select Case saveFileDialog1.FilterIndex
            Case 1
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Jpeg)

            Case 2
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Bmp)

            Case 3
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Gif)
          End Select

          fs.Close()
      End If
  End Sub
  ```

  ```csharp
  private void button2_Click(object sender, System.EventArgs e)
  {
      // Displays a SaveFileDialog so the user can save the Image
      // assigned to Button2.
      SaveFileDialog saveFileDialog1 = new SaveFileDialog();
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
      saveFileDialog1.Title = "Save an Image File";
      saveFileDialog1.ShowDialog();

      // If the file name is not an empty string open it for saving.
      if(saveFileDialog1.FileName != "")
      {
        // Saves the Image via a FileStream created by the OpenFile method.
        System.IO.FileStream fs =
            (System.IO.FileStream)saveFileDialog1.OpenFile();
        // Saves the Image in the appropriate ImageFormat based upon the
        // File type selected in the dialog box.
        // NOTE that the FilterIndex property is one-based.
        switch(saveFileDialog1.FilterIndex)
        {
            case 1 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Jpeg);
            break;

            case 2 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Bmp);
            break;

            case 3 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Gif);
            break;
        }

      fs.Close();
      }
  }
  ```

  ```cpp
  private:
      System::Void button2_Click(System::Object ^ sender,
        System::EventArgs ^ e)
      {
        // Displays a SaveFileDialog so the user can save the Image
        // assigned to Button2.
        SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();
        saveFileDialog1->Filter =
            "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
        saveFileDialog1->Title = "Save an Image File";
        saveFileDialog1->ShowDialog();
        // If the file name is not an empty string, open it for saving.
        if(saveFileDialog1->FileName != "")
        {
            // Saves the Image through a FileStream created by
            // the OpenFile method.
            System::IO::FileStream ^ fs =
              safe_cast\<System::IO::FileStream*>(
              saveFileDialog1->OpenFile());
            // Saves the Image in the appropriate ImageFormat based on
            // the file type selected in the dialog box.
            // Note that the FilterIndex property is one based.
            switch(saveFileDialog1->FilterIndex)
            {
              case 1 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Jpeg);
                  break;
              case 2 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Bmp);
                  break;
              case 3 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Gif);
                  break;
            }
        fs->Close();
        }
      }
  ```

  (Visual C# e Visual C++) Coloque o código a seguir no construtor do formulário para registrar o manipulador de eventos.

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  Para obter mais informações sobre como gravar fluxos de <xref:System.IO.FileStream.BeginWrite%2A> arquivos <xref:System.IO.FileStream.Write%2A>, consulte e.

  > [!NOTE]
  > Determinados controles, como o <xref:System.Windows.Forms.RichTextBox> controle, têm a capacidade de salvar arquivos. Para obter mais informações, consulte a seção “Componente SaveFileDialog” do artigo técnico da MSDN Online Library, [Código essencial para caixas de diálogo do Windows Forms](https://go.microsoft.com/fwlink/?LinkID=102575).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.SaveFileDialog>
- [Componente SaveFileDialog](savefiledialog-component-windows-forms.md)
