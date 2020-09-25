---
title: Como obter informações sobre arquivos, pastas e unidades – guia de programação em C#
description: Saiba como obter informações sobre arquivos, pastas e unidades. Consulte um exemplo de código e recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 7cbaea4dc5381a2ebeb97ce2797ffe850488e126
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170448"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="e8b76-104">Como obter informações sobre arquivos, pastas e unidades (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="e8b76-104">How to get information about files, folders, and drives  (C# Programming Guide)</span></span>

<span data-ttu-id="e8b76-105">No .NET, você pode acessar as informações do sistema de arquivos usando as seguintes classes:</span><span class="sxs-lookup"><span data-stu-id="e8b76-105">In .NET, you can access file system information by using the following classes:</span></span>  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="e8b76-106">As classes <xref:System.IO.FileInfo> e <xref:System.IO.DirectoryInfo> representam um arquivo ou diretório e contêm propriedades que expõem muitos dos atributos de arquivo que têm suporte pelo sistema de arquivos NTFS.</span><span class="sxs-lookup"><span data-stu-id="e8b76-106">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="e8b76-107">Elas também contêm métodos para abrir, fechar, mover e excluir arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="e8b76-107">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="e8b76-108">Você pode criar instâncias dessas classes passando uma cadeia de caracteres que representa o nome do arquivo, pasta ou unidade para o construtor:</span><span class="sxs-lookup"><span data-stu-id="e8b76-108">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="e8b76-109">Você também pode obter os nomes das unidades, pastas ou arquivos por meio de chamadas para <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> e <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8b76-109">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e8b76-110">As classes <xref:System.IO.Directory?displayProperty=nameWithType> e <xref:System.IO.File?displayProperty=nameWithType> fornecem métodos estáticos para recuperar informações sobre arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="e8b76-110">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b76-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8b76-111">Example</span></span>  

 <span data-ttu-id="e8b76-112">O exemplo a seguir mostra várias maneiras de acessar informações sobre arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="e8b76-112">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e8b76-113">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e8b76-113">Robust Programming</span></span>  

 <span data-ttu-id="e8b76-114">Quando você processa cadeias de caracteres do caminho especificado pelo usuário, você também deve tratar exceções para as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="e8b76-114">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
- <span data-ttu-id="e8b76-115">O nome do arquivo está malformado.</span><span class="sxs-lookup"><span data-stu-id="e8b76-115">The file name is malformed.</span></span> <span data-ttu-id="e8b76-116">Por exemplo, ele contém caracteres inválidos ou somente espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="e8b76-116">For example, it contains invalid characters or only white space.</span></span>  
  
- <span data-ttu-id="e8b76-117">O nome do arquivo é nulo.</span><span class="sxs-lookup"><span data-stu-id="e8b76-117">The file name is null.</span></span>  
  
- <span data-ttu-id="e8b76-118">O nome de arquivo é maior que o comprimento máximo definido pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="e8b76-118">The file name is longer than the system-defined maximum length.</span></span>  
  
- <span data-ttu-id="e8b76-119">O nome de arquivo contém dois-pontos (:).</span><span class="sxs-lookup"><span data-stu-id="e8b76-119">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="e8b76-120">Se o aplicativo não tem permissões suficientes para ler o arquivo especificado, o método `Exists` retorna `false` independentemente de se um caminho existe, o método não gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e8b76-120">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b76-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8b76-121">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="e8b76-122">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="e8b76-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e8b76-123">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e8b76-123">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
