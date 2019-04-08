---
title: 'Como: Localizar arquivos com um padrão específico no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: e4d40c4ad3a694b3f7e830604edf94d90cb4c395
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825320"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="81f93-102">Como: Localizar arquivos com um padrão específico no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81f93-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="81f93-103">O método <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> retorna uma coleção somente leitura de cadeias de caracteres que representam os nomes de caminho para os arquivos.</span><span class="sxs-lookup"><span data-stu-id="81f93-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="81f93-104">É possível usar o parâmetro `wildCards` para especificar um padrão específico.</span><span class="sxs-lookup"><span data-stu-id="81f93-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="81f93-105">Para incluir subdiretórios na pesquisa, configure o parâmetro `searchType` para `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="81f93-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="81f93-106">Uma coleção vazia é retornada se nenhum arquivo correspondente ao padrão especificado for encontrado.</span><span class="sxs-lookup"><span data-stu-id="81f93-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81f93-107">Para saber mais sobre como retornar uma lista de arquivos usando a classe `DirectoryInfo` do namespace `System.IO`, confira <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="81f93-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="81f93-108">Localizar arquivos com um padrão específico</span><span class="sxs-lookup"><span data-stu-id="81f93-108">To find files with a specified pattern</span></span>  
  
-   <span data-ttu-id="81f93-109">Use o método `GetFiles`, fornecendo o nome e o caminho do diretório a ser pesquisado e especificando o padrão.</span><span class="sxs-lookup"><span data-stu-id="81f93-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="81f93-110">O exemplo a seguir retorna todos os arquivos com a extensão `.dll` no diretório e os adiciona a `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="81f93-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="81f93-111">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81f93-111">.NET Framework Security</span></span>  
 <span data-ttu-id="81f93-112">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="81f93-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="81f93-113">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="81f93-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="81f93-114">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="81f93-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="81f93-115">`directory` não existe (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="81f93-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="81f93-116">`directory` aponta para um arquivo existente (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="81f93-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="81f93-117">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="81f93-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="81f93-118">Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="81f93-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="81f93-119">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="81f93-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="81f93-120">O usuário não possui as permissões necessárias (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="81f93-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f93-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81f93-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="81f93-122">Como: Localizar subdiretórios com um padrão específico</span><span class="sxs-lookup"><span data-stu-id="81f93-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="81f93-123">Solução de problemas: Lendo e gravando em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="81f93-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="81f93-124">Como: Obter a coleção de arquivos em um diretório</span><span class="sxs-lookup"><span data-stu-id="81f93-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
