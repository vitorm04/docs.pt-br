---
title: Como salvar arquivos usando o componente SaveFileDialog
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
ms.openlocfilehash: 4755d950da6726f007ae3333a558f3cafdcada9b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508154"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="e11af-102">Como salvar arquivos usando o componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="e11af-102">How to: Save Files Using the SaveFileDialog Component</span></span>
<span data-ttu-id="e11af-103">O <xref:System.Windows.Forms.SaveFileDialog> componente permite aos usuários navegar no sistema de arquivos e selecionar arquivos a serem salvos.</span><span class="sxs-lookup"><span data-stu-id="e11af-103">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="e11af-104">A caixa de diálogo retorna o caminho e o nome do arquivo que o usuário selecionou na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="e11af-104">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="e11af-105">No entanto, você deve escrever o código para efetivamente gravar os arquivos no disco.</span><span class="sxs-lookup"><span data-stu-id="e11af-105">However, you must write the code to actually write the files to disk.</span></span>  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="e11af-106">Salvar arquivos usando o componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="e11af-106">To save a file using the SaveFileDialog component</span></span>  
  
-   <span data-ttu-id="e11af-107">Exiba a caixa de diálogo **Salvar Arquivo** e chame um método para salvar o arquivo selecionado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e11af-107">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>  
  
     <span data-ttu-id="e11af-108">Use o <xref:System.Windows.Forms.SaveFileDialog> do componente <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> método para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e11af-108">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="e11af-109">Esse método fornece uma <xref:System.IO.Stream> objeto, você pode gravar.</span><span class="sxs-lookup"><span data-stu-id="e11af-109">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>  
  
     <span data-ttu-id="e11af-110">O exemplo a seguir usa o <xref:System.Windows.Forms.DialogResult> propriedade para obter o nome do arquivo e o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e11af-110">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="e11af-111">O <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> método fornece um fluxo para gravar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e11af-111">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>  
  
     <span data-ttu-id="e11af-112">No exemplo a seguir, há um <xref:System.Windows.Forms.Button> controle com uma imagem atribuída a ele.</span><span class="sxs-lookup"><span data-stu-id="e11af-112">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="e11af-113">Quando você clica no botão, um <xref:System.Windows.Forms.SaveFileDialog> componente é instanciado com um filtro que permite que os arquivos de tipo. gif,. JPEG e. bmp.</span><span class="sxs-lookup"><span data-stu-id="e11af-113">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="e11af-114">Se um arquivo desse tipo for selecionado na caixa de diálogo Salvar Arquivo, a imagem do botão será salva.</span><span class="sxs-lookup"><span data-stu-id="e11af-114">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e11af-115">Para obter ou definir a <xref:System.Windows.Forms.FileDialog.FileName%2A> propriedade, seu assembly requer um nível de privilégio concedido pela <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="e11af-115">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e11af-116">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="e11af-116">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="e11af-117">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="e11af-117">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="e11af-118">O exemplo supõe que seu formulário tem um <xref:System.Windows.Forms.Button> controlar com seu <xref:System.Windows.Forms.ButtonBase.Image%2A> propriedade definida como um arquivo do tipo. gif,. JPEG ou. bmp.</span><span class="sxs-lookup"><span data-stu-id="e11af-118">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e11af-119">O <xref:System.Windows.Forms.FileDialog> da classe <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> propriedade (que, devido à herança, faz parte do <xref:System.Windows.Forms.SaveFileDialog> classe) usa um índice baseado em um.</span><span class="sxs-lookup"><span data-stu-id="e11af-119">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="e11af-120">Isso será importante se você estiver escrevendo código para salvar dados em um formato específico (por exemplo, salvar um arquivo como texto sem formatação em vez de formato binário).</span><span class="sxs-lookup"><span data-stu-id="e11af-120">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="e11af-121">Essa propriedade é apresentada no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="e11af-121">This property is featured in the example below.</span></span>  
  
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
  
     <span data-ttu-id="e11af-122">(Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e11af-122">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     <span data-ttu-id="e11af-123">Para obter mais informações sobre como escrever fluxos de arquivos, consulte <xref:System.IO.FileStream.BeginWrite%2A> e <xref:System.IO.FileStream.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="e11af-123">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e11af-124">Alguns controles, como o <xref:System.Windows.Forms.RichTextBox> , têm a capacidade de salvar arquivos.</span><span class="sxs-lookup"><span data-stu-id="e11af-124">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span> <span data-ttu-id="e11af-125">Para obter mais informações, consulte a seção “Componente SaveFileDialog” do artigo técnico da MSDN Online Library, [Código essencial para caixas de diálogo do Windows Forms](https://go.microsoft.com/fwlink/?LinkID=102575).</span><span class="sxs-lookup"><span data-stu-id="e11af-125">For more information, see the "SaveFileDialog Component" section of the MSDN Online Library technical article, [Essential Code for Windows Forms Dialog Boxes](https://go.microsoft.com/fwlink/?LinkID=102575).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e11af-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e11af-126">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="e11af-127">Componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="e11af-127">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
