---
title: Como excluir um arquivo
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 57182f1a1d92b7fe954fd26b32c5e4b1107823ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348787"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="d5586-102">Como excluir um arquivo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5586-102">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="d5586-103">O método `DeleteFile` do objeto `My.Computer.FileSystem` permite a exclusão de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d5586-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="d5586-104">As opções oferecidas são: enviar um arquivo excluído para a **Lixeira**, solicitar do usuário uma confirmação de que o arquivo deve ser excluído e o que fazer quando o usuário cancela a operação.</span><span class="sxs-lookup"><span data-stu-id="d5586-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="d5586-105">Excluir um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="d5586-105">To delete a text file</span></span>  
  
- <span data-ttu-id="d5586-106">Use o método `DeleteFile` para excluir o arquivo.</span><span class="sxs-lookup"><span data-stu-id="d5586-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="d5586-107">O código a seguir demonstra como excluir o arquivo com o nome `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="d5586-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="d5586-108">Excluir um arquivo de texto e solicitar do usuário uma confirmação de que o arquivo deve ser excluído</span><span class="sxs-lookup"><span data-stu-id="d5586-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="d5586-109">Use o método `DeleteFile` para excluir o arquivo, configurando `showUI` para `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="d5586-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="d5586-110">O código a seguir demonstra como excluir o arquivo com o nome `test.txt` e permitir que o usuário confirme se o arquivo deve ser excluído.</span><span class="sxs-lookup"><span data-stu-id="d5586-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="d5586-111">Excluir um arquivo de texto e enviá-lo para a Lixeira</span><span class="sxs-lookup"><span data-stu-id="d5586-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="d5586-112">Use o método `DeleteFile` para excluir o arquivo, especificando `SendToRecycleBin` para o parâmetro `recycle`.</span><span class="sxs-lookup"><span data-stu-id="d5586-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="d5586-113">O código a seguir demonstra como excluir o arquivo com o nome `test.txt` e enviá-lo para a **Lixeira**.</span><span class="sxs-lookup"><span data-stu-id="d5586-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d5586-114">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="d5586-114">Robust Programming</span></span>  

 <span data-ttu-id="d5586-115">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="d5586-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d5586-116">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="d5586-117">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="d5586-118">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d5586-119">Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="d5586-120">O arquivo está sendo usado (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="d5586-121">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="d5586-122">O arquivo não existe (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="d5586-123">O usuário não tem permissão para excluir o arquivo ou o arquivo é somente leitura (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="d5586-124">Há uma situação de confiança parcial na qual o usuário não tem permissões suficientes (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="d5586-125">O usuário cancelou a operação e `onUserCancel` está definido como `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="d5586-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5586-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5586-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="d5586-127">Como obter a coleção de arquivos em um diretório</span><span class="sxs-lookup"><span data-stu-id="d5586-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
