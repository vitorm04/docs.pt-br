---
title: "Como localizar arquivos e diretórios existentes no armazenamento isolado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 656c390358b6f6a671cf3ef11ea7be75f897d21c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="974fb-102">Como localizar arquivos e diretórios existentes no armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="974fb-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="974fb-103">Para procurar um diretório no armazenamento isolado, use o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="974fb-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="974fb-104">Esse método usa uma cadeia de caracteres que representa um padrão de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="974fb-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="974fb-105">Você pode usar o caractere único (?) e vários caracteres (*) caracteres curinga no padrão de pesquisa, mas os caracteres curinga devem aparecer na parte final do nome.</span><span class="sxs-lookup"><span data-stu-id="974fb-105">You can use both single-character (?) and multi-character (*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="974fb-106">Por exemplo, `directory1/*ect*` é uma cadeia de caracteres de pesquisa válida, mas `*ect*/directory2` não é.</span><span class="sxs-lookup"><span data-stu-id="974fb-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="974fb-107">Para procurar um arquivo, use o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="974fb-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="974fb-108">A restrição para caracteres curinga em cadeias de caracteres de pesquisa que se aplica a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> também se aplica a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="974fb-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="974fb-109">Nenhum desses métodos é recursiva; o <xref:System.IO.IsolatedStorage.IsolatedStorageFile> classe fornece métodos para listar todos os diretórios ou arquivos no seu armazenamento.</span><span class="sxs-lookup"><span data-stu-id="974fb-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="974fb-110">No entanto, os métodos de recursiva são mostrados no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="974fb-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="974fb-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="974fb-111">Example</span></span>  
 <span data-ttu-id="974fb-112">O exemplo de código a seguir ilustra como criar arquivos e diretórios em um armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="974fb-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="974fb-113">Primeiro, um armazenamento isolado para usuário, domínio e assembly é recuperado e colocado no `isoStore` variável.</span><span class="sxs-lookup"><span data-stu-id="974fb-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="974fb-114">O <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> método é usado para configurar algumas pastas diferentes e o <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> construtor cria alguns arquivos nesses diretórios.</span><span class="sxs-lookup"><span data-stu-id="974fb-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="974fb-115">O código, em seguida, executa um loop através dos resultados do `GetAllDirectories` método.</span><span class="sxs-lookup"><span data-stu-id="974fb-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="974fb-116">Esse método usa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> para localizar todos os nomes de diretório no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="974fb-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="974fb-117">Esses nomes são armazenados em uma matriz e, em seguida, `GetAllDirectories` chama a mesmo, passando em cada diretório encontrado.</span><span class="sxs-lookup"><span data-stu-id="974fb-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="974fb-118">Como resultado, todos os nomes de diretório são retornados em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="974fb-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="974fb-119">Em seguida, o código chama o `GetAllFiles` método.</span><span class="sxs-lookup"><span data-stu-id="974fb-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="974fb-120">Este método chama `GetAllDirectories` para descobrir os nomes de todos os diretórios e, em seguida, ele verifica cada diretório de arquivos usando o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> método.</span><span class="sxs-lookup"><span data-stu-id="974fb-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="974fb-121">O resultado é retornado em uma matriz para exibição.</span><span class="sxs-lookup"><span data-stu-id="974fb-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="974fb-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="974fb-122">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="974fb-123">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="974fb-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
