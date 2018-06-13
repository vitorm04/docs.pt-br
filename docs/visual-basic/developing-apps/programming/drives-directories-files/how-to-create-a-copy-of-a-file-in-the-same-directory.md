---
title: Como criar uma cópia de um arquivo no mesmo diretório no Visual Basic
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 1147e89292181060589b38be2972e2ff1a3e386c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588928"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="e6f57-102">Como criar uma cópia de um arquivo no mesmo diretório no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6f57-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>
<span data-ttu-id="e6f57-103">Use o método `My.Computer.FileSystem.CopyFile` para copiar arquivos.</span><span class="sxs-lookup"><span data-stu-id="e6f57-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="e6f57-104">Os parâmetros permitem substituir os arquivos existentes, renomear o arquivo, mostrar o progresso da operação e permitir que o usuário cancele a operação.</span><span class="sxs-lookup"><span data-stu-id="e6f57-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="e6f57-105">Para criar uma cópia de um arquivo na mesma pasta</span><span class="sxs-lookup"><span data-stu-id="e6f57-105">To create a copy of a file in the same folder</span></span>  
  
-   <span data-ttu-id="e6f57-106">Use o método `CopyFile`, fornecendo o arquivo e o local de destino.</span><span class="sxs-lookup"><span data-stu-id="e6f57-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="e6f57-107">O exemplo a seguir cria uma cópia do `test.txt` chamada `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="e6f57-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="e6f57-108">Para criar uma cópia de um arquivo na mesma pasta, sobrescrevendo arquivos existentes</span><span class="sxs-lookup"><span data-stu-id="e6f57-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
-   <span data-ttu-id="e6f57-109">Use o método `CopyFile`, fornecendo o arquivo e o local de destino e configurando `overwrite` como `True`.</span><span class="sxs-lookup"><span data-stu-id="e6f57-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="e6f57-110">O exemplo a seguir cria uma cópia do `test.txt` com o nome `test2.txt` e substitui os arquivos existentes com este nome.</span><span class="sxs-lookup"><span data-stu-id="e6f57-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e6f57-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e6f57-111">Robust Programming</span></span>  
 <span data-ttu-id="e6f57-112">As seguintes condições podem causar o lançamento de uma exceção:</span><span class="sxs-lookup"><span data-stu-id="e6f57-112">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="e6f57-113">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e6f57-114">O sistema não conseguiu recuperar o caminho absoluto (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e6f57-115">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="e6f57-116">O arquivo de origem não é válido ou não existe (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="e6f57-117">O caminho combinado aponta para um diretório existente (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e6f57-118">O arquivo de destino já existe e `overwrite` está definido como `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e6f57-119">O usuário não tem permissões suficientes para acessar o arquivo (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e6f57-120">Um arquivo na pasta de destino com o mesmo nome está sendo usado (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e6f57-121">Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="e6f57-122">`ShowUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e o usuário cancelou a operação (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="e6f57-123">`ShowUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e ocorreu um erro de E/S não especificado (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="e6f57-124">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="e6f57-125">O usuário não tem a permissão necessária (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="e6f57-126">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="e6f57-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f57-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6f57-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [<span data-ttu-id="e6f57-128">Como copiar arquivos com um padrão específico para um diretório</span><span class="sxs-lookup"><span data-stu-id="e6f57-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [<span data-ttu-id="e6f57-129">Como criar uma cópia de um arquivo em um diretório diferente</span><span class="sxs-lookup"><span data-stu-id="e6f57-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [<span data-ttu-id="e6f57-130">Como copiar um diretório para outro diretório</span><span class="sxs-lookup"><span data-stu-id="e6f57-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [<span data-ttu-id="e6f57-131">Como renomear um arquivo</span><span class="sxs-lookup"><span data-stu-id="e6f57-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
