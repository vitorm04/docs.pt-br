---
title: Como localizar arquivos e diretórios existentes no armazenamento isolado
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09c112374458b70a464291e898e9a880c8679773
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47398950"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="d365a-102">Como localizar arquivos e diretórios existentes no armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="d365a-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="d365a-103">Para procurar um diretório no armazenamento isolado, use o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d365a-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d365a-104">Esse método usa uma cadeia de caracteres que representa um padrão de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d365a-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="d365a-105">Você pode usar o caractere único (?) e vários caracteres (\*) caracteres curinga no padrão de pesquisa, mas os caracteres curinga devem aparecer na parte final do nome.</span><span class="sxs-lookup"><span data-stu-id="d365a-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="d365a-106">Por exemplo, `directory1/*ect*` é uma cadeia de caracteres de pesquisa válida, mas `*ect*/directory2` não é.</span><span class="sxs-lookup"><span data-stu-id="d365a-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="d365a-107">Para procurar um arquivo, use o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d365a-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d365a-108">A restrição para caracteres curinga em cadeias de caracteres de pesquisa que se aplica a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> também se aplica a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="d365a-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="d365a-109">Nenhum desses métodos é recursivo; a classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> fornece métodos para listar todos os diretórios ou arquivos no repositório.</span><span class="sxs-lookup"><span data-stu-id="d365a-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="d365a-110">No entanto, os métodos recursivos são mostrados no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d365a-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d365a-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d365a-111">Example</span></span>  
 <span data-ttu-id="d365a-112">O exemplo de código a seguir ilustra como criar arquivos e diretórios em um repositório isolado.</span><span class="sxs-lookup"><span data-stu-id="d365a-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="d365a-113">Primeiro, um repositório isolado para usuário, domínio e assembly é recuperado e colocado na variável `isoStore`.</span><span class="sxs-lookup"><span data-stu-id="d365a-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="d365a-114">O método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> é usado para configurar algumas pastas diferentes, e o construtor <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> cria alguns arquivos nesses diretórios.</span><span class="sxs-lookup"><span data-stu-id="d365a-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="d365a-115">O código executa um loop através dos resultados do método `GetAllDirectories`.</span><span class="sxs-lookup"><span data-stu-id="d365a-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="d365a-116">Esse método usa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> para localizar todos os nomes de diretório no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d365a-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="d365a-117">Esses nomes são armazenados em uma matriz, e `GetAllDirectories` chama a si mesmo, passando cada diretório encontrado.</span><span class="sxs-lookup"><span data-stu-id="d365a-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="d365a-118">Como resultado, todos os nomes de diretório são retornados em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="d365a-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="d365a-119">Em seguida, o código chama o método `GetAllFiles`.</span><span class="sxs-lookup"><span data-stu-id="d365a-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="d365a-120">Este método chama `GetAllDirectories` para descobrir os nomes de todos os diretórios e verifica cada diretório de arquivos usando o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="d365a-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="d365a-121">O resultado é retornado em uma matriz para exibição.</span><span class="sxs-lookup"><span data-stu-id="d365a-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="d365a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d365a-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [<span data-ttu-id="d365a-123">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="d365a-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
