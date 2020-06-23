---
title: Como salvar arquivos usando o componente SaveFileDialog
description: Saiba como usar o componente SaveFileDialog para procurar o sistema de arquivos e selecionar os arquivos a serem salvos.
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
ms.openlocfilehash: cd773c3d4aa2b907eb09dd87c3fdbe138bf533bb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904397"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="88c8f-103">Como salvar arquivos usando o componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="88c8f-103">How to: Save Files Using the SaveFileDialog Component</span></span>

<span data-ttu-id="88c8f-104">O <xref:System.Windows.Forms.SaveFileDialog> componente permite que os usuários procurem o sistema de arquivos e selecionem os arquivos a serem salvos.</span><span class="sxs-lookup"><span data-stu-id="88c8f-104">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="88c8f-105">A caixa de diálogo retorna o caminho e o nome do arquivo que o usuário selecionou na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="88c8f-105">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="88c8f-106">No entanto, você deve escrever o código para efetivamente gravar os arquivos no disco.</span><span class="sxs-lookup"><span data-stu-id="88c8f-106">However, you must write the code to actually write the files to disk.</span></span>

### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="88c8f-107">Salvar arquivos usando o componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="88c8f-107">To save a file using the SaveFileDialog component</span></span>

- <span data-ttu-id="88c8f-108">Exiba a caixa de diálogo **Salvar Arquivo** e chame um método para salvar o arquivo selecionado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="88c8f-108">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>

  <span data-ttu-id="88c8f-109">Use o <xref:System.Windows.Forms.SaveFileDialog> método do componente <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="88c8f-109">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="88c8f-110">Esse método fornece um <xref:System.IO.Stream> objeto no qual você pode gravar.</span><span class="sxs-lookup"><span data-stu-id="88c8f-110">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>

  <span data-ttu-id="88c8f-111">O exemplo a seguir usa a <xref:System.Windows.Forms.DialogResult> propriedade para obter o nome do arquivo e o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="88c8f-111">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="88c8f-112">O <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> método fornece um fluxo no qual gravar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="88c8f-112">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>

  <span data-ttu-id="88c8f-113">No exemplo a seguir, há um <xref:System.Windows.Forms.Button> controle com uma imagem atribuída a ele.</span><span class="sxs-lookup"><span data-stu-id="88c8f-113">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="88c8f-114">Quando você clica no botão, um <xref:System.Windows.Forms.SaveFileDialog> componente é instanciado com um filtro que permite arquivos do tipo. gif,. jpeg e. bmp.</span><span class="sxs-lookup"><span data-stu-id="88c8f-114">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="88c8f-115">Se um arquivo desse tipo for selecionado na caixa de diálogo Salvar Arquivo, a imagem do botão será salva.</span><span class="sxs-lookup"><span data-stu-id="88c8f-115">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="88c8f-116">Para obter ou definir a <xref:System.Windows.Forms.FileDialog.FileName%2A> propriedade, seu assembly requer um nível de privilégio concedido pela <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="88c8f-116">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="88c8f-117">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="88c8f-117">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="88c8f-118">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="88c8f-118">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

  <span data-ttu-id="88c8f-119">O exemplo supõe que seu formulário tenha um <xref:System.Windows.Forms.Button> controle com sua <xref:System.Windows.Forms.ButtonBase.Image%2A> propriedade definida como um arquivo de Type. gif,. jpeg ou. bmp.</span><span class="sxs-lookup"><span data-stu-id="88c8f-119">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>

  > [!NOTE]
  > <span data-ttu-id="88c8f-120">A <xref:System.Windows.Forms.FileDialog> propriedade da classe <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> (que, devido à herança, faz parte da <xref:System.Windows.Forms.SaveFileDialog> classe) usa um índice baseado em um.</span><span class="sxs-lookup"><span data-stu-id="88c8f-120">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="88c8f-121">Isso será importante se você estiver escrevendo código para salvar dados em um formato específico (por exemplo, salvar um arquivo como texto sem formatação em vez de formato binário).</span><span class="sxs-lookup"><span data-stu-id="88c8f-121">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="88c8f-122">Essa propriedade é apresentada no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="88c8f-122">This property is featured in the example below.</span></span>

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

  <span data-ttu-id="88c8f-123">(Visual C# e Visual C++) Coloque o código a seguir no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="88c8f-123">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  <span data-ttu-id="88c8f-124">Para obter mais informações sobre como gravar fluxos de arquivos, consulte <xref:System.IO.FileStream.BeginWrite%2A> e <xref:System.IO.FileStream.Write%2A> .</span><span class="sxs-lookup"><span data-stu-id="88c8f-124">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>

  > [!NOTE]
  > <span data-ttu-id="88c8f-125">Determinados controles, como o <xref:System.Windows.Forms.RichTextBox> controle, têm a capacidade de salvar arquivos.</span><span class="sxs-lookup"><span data-stu-id="88c8f-125">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span>

## <a name="see-also"></a><span data-ttu-id="88c8f-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="88c8f-126">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="88c8f-127">Componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="88c8f-127">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
