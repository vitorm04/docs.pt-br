---
title: 'Como: Salvar arquivos com o controle RichTextBox dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: c9a5d471a58c646c786cf441ee7d7ec235788f10
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723017"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="ee79d-102">Como: Salvar arquivos com o controle RichTextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee79d-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="ee79d-103">Os formulários do Windows <xref:System.Windows.Forms.RichTextBox> controle pode gravar as informações exibidas em um dos vários formatos:</span><span class="sxs-lookup"><span data-stu-id="ee79d-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
-   <span data-ttu-id="ee79d-104">Texto sem formatação</span><span class="sxs-lookup"><span data-stu-id="ee79d-104">Plain text</span></span>  
  
-   <span data-ttu-id="ee79d-105">Texto sem formatação Unicode</span><span class="sxs-lookup"><span data-stu-id="ee79d-105">Unicode plain text</span></span>  
  
-   <span data-ttu-id="ee79d-106">RTF (Formato Rich Text)</span><span class="sxs-lookup"><span data-stu-id="ee79d-106">Rich-Text Format (RTF)</span></span>  
  
-   <span data-ttu-id="ee79d-107">RTF com espaços em vez de objetos OLE</span><span class="sxs-lookup"><span data-stu-id="ee79d-107">RTF with spaces in place of OLE objects</span></span>  
  
-   <span data-ttu-id="ee79d-108">Texto sem formatação com uma representação textual de objetos OLE</span><span class="sxs-lookup"><span data-stu-id="ee79d-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="ee79d-109">Para salvar um arquivo, chame o <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ee79d-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="ee79d-110">Você também pode usar o método **SaveFile** para salvar dados em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="ee79d-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="ee79d-111">Para obter mais informações, consulte <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="ee79d-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="ee79d-112">Para salvar o conteúdo do controle em um arquivo</span><span class="sxs-lookup"><span data-stu-id="ee79d-112">To save the contents of the control to a file</span></span>  
  
1.  <span data-ttu-id="ee79d-113">Determine o caminho do arquivo a ser salvo.</span><span class="sxs-lookup"><span data-stu-id="ee79d-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="ee79d-114">Para fazer isso em um aplicativo do mundo real, você normalmente usaria o <xref:System.Windows.Forms.SaveFileDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="ee79d-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="ee79d-115">Para obter uma visão geral, consulte [Visão geral do componente SaveFileDialog](savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ee79d-115">For an overview, see [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="ee79d-116">Chame o <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> método da <xref:System.Windows.Forms.RichTextBox> controle, especificando o arquivo a ser salvo e, opcionalmente, um tipo de arquivo.</span><span class="sxs-lookup"><span data-stu-id="ee79d-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="ee79d-117">Se você chamar o método com um nome de arquivo como seu único argumento, o arquivo será salvo como RTF.</span><span class="sxs-lookup"><span data-stu-id="ee79d-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="ee79d-118">Para especificar outro tipo de arquivo, chame o método com um valor da <xref:System.Windows.Forms.RichTextBoxStreamType> enumeração como seu segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="ee79d-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="ee79d-119">No exemplo de código a seguir, o caminho definido para o do arquivo rich-text é a pasta **Meus documentos**.</span><span class="sxs-lookup"><span data-stu-id="ee79d-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="ee79d-120">Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta.</span><span class="sxs-lookup"><span data-stu-id="ee79d-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="ee79d-121">Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem com mais segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee79d-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="ee79d-122">O exemplo a seguir supõe um formulário com um <xref:System.Windows.Forms.RichTextBox> controle já adicionado.</span><span class="sxs-lookup"><span data-stu-id="ee79d-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ee79d-123">Este exemplo cria um novo arquivo, se o arquivo ainda não existe.</span><span class="sxs-lookup"><span data-stu-id="ee79d-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="ee79d-124">Se um aplicativo precisar criar um arquivo, essa aplicativo precisará de acesso Criar para a pasta.</span><span class="sxs-lookup"><span data-stu-id="ee79d-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="ee79d-125">As permissões são definidas usando listas de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="ee79d-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="ee79d-126">Se o arquivo já existir, o aplicativo precisará apenas de acesso Gravar, um privilégio menor.</span><span class="sxs-lookup"><span data-stu-id="ee79d-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="ee79d-127">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso de leitura a um único arquivo, em vez de acesso Criar a uma pasta.</span><span class="sxs-lookup"><span data-stu-id="ee79d-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="ee79d-128">Além disso, é mais seguro gravar dados em pastas de usuário do que na pasta raiz ou na pasta Arquivos de Programas.</span><span class="sxs-lookup"><span data-stu-id="ee79d-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee79d-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee79d-129">See also</span></span>
- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="ee79d-130">Controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ee79d-130">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="ee79d-131">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee79d-131">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
