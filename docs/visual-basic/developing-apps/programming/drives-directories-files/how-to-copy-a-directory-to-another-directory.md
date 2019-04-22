---
title: 'Como: Copiar um diretório para outro diretório no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: e45de705eb25d58857239cc549125c524765aaa5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816571"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="106d0-102">Como: Copiar um diretório para outro diretório no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="106d0-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>
<span data-ttu-id="106d0-103">Use o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> para copiar um diretório para outro diretório.</span><span class="sxs-lookup"><span data-stu-id="106d0-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="106d0-104">Esse método copia o conteúdo do diretório, bem como o próprio diretório.</span><span class="sxs-lookup"><span data-stu-id="106d0-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="106d0-105">Se o diretório de destino não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="106d0-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="106d0-106">Se existir um diretório com o mesmo nome no local de destino e `overwrite` estiver definido como `False`, o conteúdo dos dois diretórios será mesclado.</span><span class="sxs-lookup"><span data-stu-id="106d0-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="106d0-107">Você pode especificar um novo nome para o diretório durante a operação.</span><span class="sxs-lookup"><span data-stu-id="106d0-107">You can specify a new name for the directory during the operation.</span></span>  
  
 <span data-ttu-id="106d0-108">Ao copiar arquivos em um diretório, podem ser geradas exceções que são causadas pelo arquivo específico, como um arquivo existente durante a mesclagem enquanto `overwrite` é definido como `False`.</span><span class="sxs-lookup"><span data-stu-id="106d0-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="106d0-109">Quando essas exceções são lançadas, elas são consolidadas em uma única exceção, cuja propriedade `Data` contém entradas em que o caminho do arquivo ou do diretório é a chave e a mensagem de exceção específica está contida no valor correspondente.</span><span class="sxs-lookup"><span data-stu-id="106d0-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>  
  
### <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="106d0-110">Para copiar um diretório para outro diretório</span><span class="sxs-lookup"><span data-stu-id="106d0-110">To copy a directory to another directory</span></span>  
  
-   <span data-ttu-id="106d0-111">Use o método `CopyDirectory`, especificando nomes de diretório de origem e destino.</span><span class="sxs-lookup"><span data-stu-id="106d0-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="106d0-112">O exemplo a seguir copia o diretório denominado `TestDirectory1` para `TestDirectory2`, substituindo arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="106d0-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]  
  
     <span data-ttu-id="106d0-113">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="106d0-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="106d0-114">No selecionador de snippet de código, ele está localizado em **Sistema de Arquivos – Processando Unidades, Pastas e Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="106d0-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="106d0-115">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="106d0-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="106d0-116">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="106d0-116">Robust Programming</span></span>  
 <span data-ttu-id="106d0-117">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="106d0-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="106d0-118">O novo nome especificado para o diretório contém dois pontos (:) ou barra (\ ou /) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="106d0-119">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="106d0-120">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="106d0-121">`destinationDirectoryName` é `Nothing` ou é uma cadeia de caracteres vazia (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="106d0-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="106d0-122">O diretório de origem não existe (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="106d0-123">O diretório de origem é um diretório raiz (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="106d0-124">O caminho combinado aponta para um arquivo existente (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="106d0-125">O caminho de origem e o caminho de destino são os mesmos (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="106d0-126">`ShowUI` está definido como `UIOption.AllDialogs` e o usuário cancelou a operação ou um ou mais arquivos no diretório não podem ser copiados (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="106d0-127">A operação é cíclica (<xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>  
  
-   <span data-ttu-id="106d0-128">O caminho contém dois pontos (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="106d0-129">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="106d0-130">Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="106d0-131">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="106d0-132">Um arquivo de destino existe, mas não pode ser acessado (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="106d0-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="106d0-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="106d0-133">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [<span data-ttu-id="106d0-134">Como: Localizar subdiretórios com um padrão específico</span><span class="sxs-lookup"><span data-stu-id="106d0-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="106d0-135">Como: Obter a coleção de arquivos em um diretório</span><span class="sxs-lookup"><span data-stu-id="106d0-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
