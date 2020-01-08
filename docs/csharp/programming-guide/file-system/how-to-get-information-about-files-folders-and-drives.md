---
title: Como obter informações sobre arquivos, pastas e unidades – guia de C# programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: e8bd65b1c8c24f69d280cf69deaf25daf7cf8818
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635386"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="de19b-102">Como obter informações sobre arquivos, pastas e unidades (guia deC# programação)</span><span class="sxs-lookup"><span data-stu-id="de19b-102">How to get information about files, folders, and drives  (C# Programming Guide)</span></span>
<span data-ttu-id="de19b-103">No .NET Framework, você pode acessar informações do sistema de arquivos usando as classes a seguir:</span><span class="sxs-lookup"><span data-stu-id="de19b-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="de19b-104">As classes <xref:System.IO.FileInfo> e <xref:System.IO.DirectoryInfo> representam um arquivo ou diretório e contêm propriedades que expõem muitos dos atributos de arquivo que têm suporte pelo sistema de arquivos NTFS.</span><span class="sxs-lookup"><span data-stu-id="de19b-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="de19b-105">Elas também contêm métodos para abrir, fechar, mover e excluir arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="de19b-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="de19b-106">Você pode criar instâncias dessas classes passando uma cadeia de caracteres que representa o nome do arquivo, pasta ou unidade para o construtor:</span><span class="sxs-lookup"><span data-stu-id="de19b-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="de19b-107">Você também pode obter os nomes das unidades, pastas ou arquivos por meio de chamadas para <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> e <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de19b-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="de19b-108">As classes <xref:System.IO.Directory?displayProperty=nameWithType> e <xref:System.IO.File?displayProperty=nameWithType> fornecem métodos estáticos para recuperar informações sobre arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="de19b-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de19b-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de19b-109">Example</span></span>  
 <span data-ttu-id="de19b-110">O exemplo a seguir mostra várias maneiras de acessar informações sobre arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="de19b-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="de19b-111">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="de19b-111">Robust Programming</span></span>  
 <span data-ttu-id="de19b-112">Quando você processa cadeias de caracteres do caminho especificado pelo usuário, você também deve tratar exceções para as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="de19b-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
- <span data-ttu-id="de19b-113">O nome do arquivo está malformado.</span><span class="sxs-lookup"><span data-stu-id="de19b-113">The file name is malformed.</span></span> <span data-ttu-id="de19b-114">Por exemplo, ele contém caracteres inválidos ou somente espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="de19b-114">For example, it contains invalid characters or only white space.</span></span>  
  
- <span data-ttu-id="de19b-115">O nome do arquivo é nulo.</span><span class="sxs-lookup"><span data-stu-id="de19b-115">The file name is null.</span></span>  
  
- <span data-ttu-id="de19b-116">O nome de arquivo é maior que o comprimento máximo definido pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="de19b-116">The file name is longer than the system-defined maximum length.</span></span>  
  
- <span data-ttu-id="de19b-117">O nome de arquivo contém dois-pontos (:).</span><span class="sxs-lookup"><span data-stu-id="de19b-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="de19b-118">Se o aplicativo não tem permissões suficientes para ler o arquivo especificado, o método `Exists` retorna `false` independentemente de se um caminho existe, o método não gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="de19b-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de19b-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="de19b-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="de19b-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="de19b-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="de19b-121">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="de19b-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
