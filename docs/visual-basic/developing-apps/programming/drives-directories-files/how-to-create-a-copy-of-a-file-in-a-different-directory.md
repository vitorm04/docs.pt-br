---
title: Como criar uma cópia de um arquivo em um diretório diferente
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348840"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="292cf-102">Como criar uma cópia de um arquivo em um diretório diferente no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="292cf-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>

<span data-ttu-id="292cf-103">O método `My.Computer.FileSystem.CopyFile` permite a cópia de arquivos.</span><span class="sxs-lookup"><span data-stu-id="292cf-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="292cf-104">Os parâmetros desse método oferecem a capacidade de substituir os arquivos existentes, renomear o arquivo, mostrar o progresso da operação e permitir que o usuário cancele a operação.</span><span class="sxs-lookup"><span data-stu-id="292cf-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="292cf-105">Copiar um arquivo de texto para outra pasta</span><span class="sxs-lookup"><span data-stu-id="292cf-105">To copy a text file to another folder</span></span>  
  
- <span data-ttu-id="292cf-106">Use o método `CopyFile` para copiar um arquivo, especificando o arquivo de origem e o diretório de destino.</span><span class="sxs-lookup"><span data-stu-id="292cf-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="292cf-107">O parâmetro `overwrite` permite especificar se os arquivos existentes devem ser sobrescritos ou não.</span><span class="sxs-lookup"><span data-stu-id="292cf-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="292cf-108">Os exemplos de código a seguir demonstram como usar `CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="292cf-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="292cf-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="292cf-109">Robust Programming</span></span>  

 <span data-ttu-id="292cf-110">As seguintes condições podem causar o lançamento de uma exceção:</span><span class="sxs-lookup"><span data-stu-id="292cf-110">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="292cf-111">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="292cf-112">O sistema não conseguiu recuperar o caminho absoluto (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="292cf-113">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="292cf-114">O arquivo de origem não é válido ou não existe (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="292cf-115">O caminho combinado aponta para um diretório existente (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="292cf-116">O arquivo de destino já existe e `overwrite` está definido como `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="292cf-117">O usuário não tem permissões suficientes para acessar o arquivo (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="292cf-118">Um arquivo na pasta de destino com o mesmo nome está sendo usado (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="292cf-119">Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="292cf-120">`ShowUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e o usuário cancelou a operação (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="292cf-121">`ShowUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e ocorreu um erro de E/S não especificado (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="292cf-122">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="292cf-123">O usuário não tem a permissão necessária (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="292cf-124">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="292cf-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292cf-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="292cf-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="292cf-126">Como copiar arquivos com um padrão específico para um diretório</span><span class="sxs-lookup"><span data-stu-id="292cf-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="292cf-127">Como criar uma cópia de um arquivo no mesmo diretório</span><span class="sxs-lookup"><span data-stu-id="292cf-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="292cf-128">Como copiar um diretório para outro diretório</span><span class="sxs-lookup"><span data-stu-id="292cf-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="292cf-129">Como renomear um arquivo</span><span class="sxs-lookup"><span data-stu-id="292cf-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
