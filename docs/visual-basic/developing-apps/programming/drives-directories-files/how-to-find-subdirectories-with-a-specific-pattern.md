---
title: 'Como: Localizar subdiretórios com um padrão específico no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 705fa6e40d0e6d18826966e3f10cfd31d9e7a6ff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823396"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="3fdb5-102">Como: Localizar subdiretórios com um padrão específico no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fdb5-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="3fdb5-103">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> retorna uma coleção somente leitura de cadeias de caracteres que representam os nomes de caminho para os subdiretórios em um diretório.</span><span class="sxs-lookup"><span data-stu-id="3fdb5-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="3fdb5-104">É possível usar o parâmetro `wildCards` para especificar um padrão específico.</span><span class="sxs-lookup"><span data-stu-id="3fdb5-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="3fdb5-105">Caso deseje incluir os conteúdos dos subdiretórios na pesquisa, defina o parâmetro `searchType` para `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="3fdb5-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="3fdb5-106">Uma coleção vazia será retornada se nenhum diretório correspondente ao padrão especificado for encontrado.</span><span class="sxs-lookup"><span data-stu-id="3fdb5-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="3fdb5-107">Localizar subdiretórios com um padrão específico</span><span class="sxs-lookup"><span data-stu-id="3fdb5-107">To find subdirectories with a specific pattern</span></span>  
  
-   <span data-ttu-id="3fdb5-108">Use o método `GetDirectories`, fornecendo o nome e o caminho do diretório a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="3fdb5-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="3fdb5-109">O exemplo a seguir retorna todos os diretórios na estrutura de diretório que contém a palavra “Logs” em seu nome e as adiciona a `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="3fdb5-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3fdb5-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="3fdb5-110">Robust Programming</span></span>  
 <span data-ttu-id="3fdb5-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="3fdb5-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3fdb5-112">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="3fdb5-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="3fdb5-113">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="3fdb5-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="3fdb5-114">Um ou mais dos caracteres curinga especificados é `Nothing`, uma cadeia de caracteres vazia ou contém somente espaços (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="3fdb5-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="3fdb5-115">`directory` não existe (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="3fdb5-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="3fdb5-116">`directory` aponta para um arquivo existente (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3fdb5-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="3fdb5-117">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="3fdb5-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="3fdb5-118">Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="3fdb5-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="3fdb5-119">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="3fdb5-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="3fdb5-120">O usuário não possui as permissões necessárias (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="3fdb5-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fdb5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fdb5-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="3fdb5-122">Como: Localizar arquivos com um padrão específico</span><span class="sxs-lookup"><span data-stu-id="3fdb5-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
