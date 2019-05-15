---
title: 'Como: Baixar um arquivo no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 2beab73bde30a11ed9803723dce5fb4c3392fce7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662734"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="6db57-102">Como: Baixar um arquivo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6db57-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="6db57-103">O método <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> pode ser usado para baixar um arquivo remoto e armazená-lo em um local específico.</span><span class="sxs-lookup"><span data-stu-id="6db57-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="6db57-104">Se o parâmetro `ShowUI` for definido como `True`, uma caixa de diálogo será exibida mostrando o andamento do download e permitindo que os usuários cancelem a operação.</span><span class="sxs-lookup"><span data-stu-id="6db57-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="6db57-105">Por padrão, os arquivos existentes com o mesmo nome não são sobrescritos. Se você deseja sobrescrever os arquivos existentes, defina o parâmetro `overwrite` como `True`.</span><span class="sxs-lookup"><span data-stu-id="6db57-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="6db57-106">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="6db57-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6db57-107">O nome da unidade não é válido (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="6db57-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="6db57-108">A autenticação necessária não foi fornecida (<xref:System.UnauthorizedAccessException> ou <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="6db57-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="6db57-109">O servidor não responde dentro do `connectionTimeout` especificado (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="6db57-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
- <span data-ttu-id="6db57-110">A solicitação foi negada pelo site (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="6db57-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="6db57-111">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6db57-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="6db57-112">Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6db57-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="6db57-113">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6db57-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="6db57-114">O conteúdo do arquivo pode não ser esperado, e os métodos para ler o arquivo podem falhar.</span><span class="sxs-lookup"><span data-stu-id="6db57-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="6db57-115">Para baixar um arquivo</span><span class="sxs-lookup"><span data-stu-id="6db57-115">To download a file</span></span>  
  
- <span data-ttu-id="6db57-116">Use o método `DownloadFile` para baixar o arquivo, especificando o local do arquivo de destino como uma cadeia de caracteres ou URI e especificando o local no qual armazenar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="6db57-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="6db57-117">Este exemplo baixa o arquivo `WineList.txt` de `http://www.cohowinery.com/downloads` e salva-o em `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="6db57-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="6db57-118">Para baixar um arquivo, especificando um intervalo de tempo limite</span><span class="sxs-lookup"><span data-stu-id="6db57-118">To download a file, specifying a time-out interval</span></span>  
  
- <span data-ttu-id="6db57-119">Use o método `DownloadFile` para baixar o arquivo, especificando o local do arquivo de destino como uma cadeia de caracteres ou URI, especificando o local no qual armazenar o arquivo e especificando o intervalo de tempo limite, em milissegundos (o padrão é 1000).</span><span class="sxs-lookup"><span data-stu-id="6db57-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="6db57-120">Este exemplo baixa o arquivo `WineList.txt` de `http://www.cohowinery.com/downloads` e salva-o em `C:\Documents and Settings\All Users\Documents`, especificando um intervalo de tempo limite de 500 milissegundos:</span><span class="sxs-lookup"><span data-stu-id="6db57-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="6db57-121">Para baixar um arquivo, fornecendo um nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="6db57-121">To download a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="6db57-122">Use o método `DownLoadFile` para baixar o arquivo, especificando o local do arquivo de destino como uma cadeia de caracteres ou URI, especificando o local no qual armazenar o arquivo e especificando o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="6db57-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="6db57-123">Este exemplo baixa o arquivo `WineList.txt` de `http://www.cohowinery.com/downloads` e salva em `C:\Documents and Settings\All Users\Documents`, com o nome de usuário `anonymous` e uma senha em branco.</span><span class="sxs-lookup"><span data-stu-id="6db57-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6db57-124">O protocolo FTP usado pelo método `DownLoadFile` envia informações, incluindo senhas, em texto sem formatação e não deve ser usado para transmitir informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="6db57-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6db57-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6db57-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="6db57-126">Como: Carregar um arquivo</span><span class="sxs-lookup"><span data-stu-id="6db57-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="6db57-127">Como: Analisar caminhos de arquivo</span><span class="sxs-lookup"><span data-stu-id="6db57-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
