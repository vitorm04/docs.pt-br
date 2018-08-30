---
title: Armazenando dados e lendo na Área de Transferência (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 7964a39bb84ac6af6b6c196c053f51c30301985c
ms.sourcegitcommit: 8c6c62ba1eefa492701e264e41890ee20fae77a3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2018
ms.locfileid: "42792338"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="43906-102">Armazenando dados e lendo na Área de Transferência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43906-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="43906-103">A Área de Transferência pode ser usada para armazenar dados, como texto e imagens.</span><span class="sxs-lookup"><span data-stu-id="43906-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="43906-104">Como a Área de Transferência é compartilhada por todos os processos ativos, ela pode ser usada para transferir dados entre eles.</span><span class="sxs-lookup"><span data-stu-id="43906-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="43906-105">O objeto `My.Computer.Clipboard` permite que você acesse facilmente a Área de Transferência e leia e grave nela.</span><span class="sxs-lookup"><span data-stu-id="43906-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="43906-106">Lendo da Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="43906-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="43906-107">Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> para ler o texto da Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="43906-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="43906-108">O código a seguir lê o texto e o mostra em uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="43906-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="43906-109">Deve haver texto armazenado na Área de Transferência para que o exemplo seja executado corretamente.</span><span class="sxs-lookup"><span data-stu-id="43906-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 <span data-ttu-id="43906-110">Este exemplo de código também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="43906-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="43906-111">No seletor de trecho de código, ele está localizado em **Aplicativos do Windows Forms > Área de Transferência**.</span><span class="sxs-lookup"><span data-stu-id="43906-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="43906-112">Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="43906-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="43906-113">Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> para recuperar uma imagem da Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="43906-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="43906-114">Este exemplo verifica se há alguma imagem na Área de Transferência antes de recuperá-la e atribuí-la à `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="43906-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 <span data-ttu-id="43906-115">Este exemplo de código também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="43906-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="43906-116">No seletor de trecho de código, ele está localizado em **Aplicativos do Windows Forms > Área de Transferência**. Para obter mais informações, consulte [Trechos de código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="43906-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="43906-117">Itens colocados na Área de Transferência persistirão mesmo após o aplicativo ser encerrado.</span><span class="sxs-lookup"><span data-stu-id="43906-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="43906-118">Determinando o tipo de arquivo armazenado na Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="43906-118">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="43906-119">Os dados na área de transferência podem ter várias formas diferentes, como texto, um arquivo de áudio ou uma imagem.</span><span class="sxs-lookup"><span data-stu-id="43906-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="43906-120">Para determinar que tipo de arquivo está na Área de Transferência, você pode usar métodos como <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> e <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="43906-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="43906-121">Você poderá usar o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> se quiser verificar um formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="43906-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="43906-122">Use a função `ContainsImage` para determinar se os dados contidos na Área de Transferência são uma imagem.</span><span class="sxs-lookup"><span data-stu-id="43906-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="43906-123">O código a seguir verifica se os dados são uma imagem e relata de acordo.</span><span class="sxs-lookup"><span data-stu-id="43906-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="43906-124">Limpando a Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="43906-124">Clearing the Clipboard</span></span>  
 <span data-ttu-id="43906-125">O método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> limpa a Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="43906-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="43906-126">Como a Área de Transferência é compartilhada por outros processos, limpá-la pode ter nesses processos.</span><span class="sxs-lookup"><span data-stu-id="43906-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="43906-127">O código a seguir mostra como usar o método `Clear`.</span><span class="sxs-lookup"><span data-stu-id="43906-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="43906-128">Gravando na Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="43906-128">Writing to the Clipboard</span></span>  
 <span data-ttu-id="43906-129">Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> para gravar texto na Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="43906-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="43906-130">O código a seguir grava a cadeia de caracteres "This is a test string" na Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="43906-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 <span data-ttu-id="43906-131">O método `SetText` pode aceitar um parâmetro de formato que contém um tipo de <xref:System.Windows.Forms.TextDataFormat>.</span><span class="sxs-lookup"><span data-stu-id="43906-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="43906-132">O código a seguir grava a cadeia de caracteres "This is a test string" na Área de Transferência como um texto RTF.</span><span class="sxs-lookup"><span data-stu-id="43906-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 <span data-ttu-id="43906-133">Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> para gravar dados na Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="43906-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="43906-134">Este exemplo grava o `DataObject` `dataChunk` na área de transferência no formato personalizado `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="43906-134">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 <span data-ttu-id="43906-135">Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> para gravar dados de áudio na Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="43906-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="43906-136">Este exemplo cria a matriz de bytes `musicReader`, lê o arquivo `cool.wav` nela e o grava na Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="43906-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="43906-137">Como a Área de Transferência pode ser acessada por outros usuários, não a use para armazenar informações confidenciais, como senhas ou dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="43906-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43906-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43906-138">See also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>  
 [<span data-ttu-id="43906-139">Como ler dados de objeto de um arquivo XML</span><span class="sxs-lookup"><span data-stu-id="43906-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="43906-140">Como gravar dados de objeto em um arquivo XML</span><span class="sxs-lookup"><span data-stu-id="43906-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
