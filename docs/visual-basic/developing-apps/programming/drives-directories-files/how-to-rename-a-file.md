---
title: 'Como: Renomear um arquivo no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3b1e85cc9e0b0768f7065ff690f6dc969ee040b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676361"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="c009f-102">Como: Renomear um arquivo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c009f-102">How to: Rename a File in Visual Basic</span></span>
<span data-ttu-id="c009f-103">Use o método `RenameFile` do objeto `My.Computer.FileSystem` para renomear um arquivo, fornecendo o local atual, o nome de arquivo e o novo nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="c009f-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="c009f-104">Esse método não pode ser usado para mover um arquivo. Use o método `MoveFile` para mover e renomear o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c009f-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="c009f-105">Para renomear um arquivo</span><span class="sxs-lookup"><span data-stu-id="c009f-105">To rename a file</span></span>  
  
-   <span data-ttu-id="c009f-106">Use o método `My.Computer.FileSystem.RenameFile` para renomear um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c009f-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="c009f-107">Este exemplo renomeia o arquivo chamado `Test.txt` para `SecondTest.txt`.</span><span class="sxs-lookup"><span data-stu-id="c009f-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 <span data-ttu-id="c009f-108">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c009f-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c009f-109">No selecionador de snippet de código, o snippet está localizado em **Sistema de Arquivos – Processando Unidades, Pastas e Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="c009f-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="c009f-110">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c009f-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c009f-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="c009f-111">Robust Programming</span></span>  
 <span data-ttu-id="c009f-112">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="c009f-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c009f-113">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="c009f-114">`newName` contém informações de caminho (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="c009f-115">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="c009f-116">`newName` é `Nothing` ou é uma cadeia de caracteres vazia (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="c009f-117">O arquivo de origem não é válido ou não existe (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="c009f-118">Há um arquivo ou diretório existente com o nome especificado em `newName` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="c009f-119">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="c009f-120">Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="c009f-121">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="c009f-122">O usuário não tem a permissão necessária (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="c009f-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c009f-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c009f-123">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="c009f-124">Como: Mover um arquivo</span><span class="sxs-lookup"><span data-stu-id="c009f-124">How to: Move a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [<span data-ttu-id="c009f-125">Criando, excluindo e movendo arquivos e diretórios</span><span class="sxs-lookup"><span data-stu-id="c009f-125">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="c009f-126">Como: Criar uma cópia de um arquivo no mesmo diretório</span><span class="sxs-lookup"><span data-stu-id="c009f-126">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="c009f-127">Como: Criar uma cópia de um arquivo em outro diretório</span><span class="sxs-lookup"><span data-stu-id="c009f-127">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
