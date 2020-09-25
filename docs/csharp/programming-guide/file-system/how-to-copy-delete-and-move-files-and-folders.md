---
title: Como copiar, excluir e mover arquivos e pastas-guia de programação em C#
description: Saiba como copiar, excluir e mover arquivos e pastas usando as classes File, Directory, FileInfo e DirectoryInfo.
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 24595c9f5c75b70afb0ff079b6b93e35502f7fb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202507"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="1294b-103">Como copiar, excluir e mover arquivos e pastas (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="1294b-103">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>

<span data-ttu-id="1294b-104">Os exemplos a seguir mostram como copiar, mover e excluir arquivos e pastas de maneira síncrona usando as classes <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType> e <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> do namespace <xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1294b-104">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1294b-105">Esses exemplos não fornecem uma barra de progresso ou qualquer outra interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1294b-105">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="1294b-106">Se você quiser fornecer uma caixa de diálogo de progresso padrão, consulte [como fornecer uma caixa de diálogo de progresso para operações de arquivo](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="1294b-106">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="1294b-107">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> para fornecer eventos que permitirão que você calcule o progresso ao operar em vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="1294b-107">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="1294b-108">Outra abordagem é usar a invocação de plataforma para invocar os métodos relacionados ao arquivo relevantes no Shell do Windows.</span><span class="sxs-lookup"><span data-stu-id="1294b-108">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="1294b-109">Para obter informações sobre como executar essas operações de arquivo de forma assíncrona, consulte [E/S de arquivo assíncrona](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="1294b-109">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1294b-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1294b-110">Example</span></span>  

 <span data-ttu-id="1294b-111">O exemplo a seguir mostra como copiar arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="1294b-111">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="1294b-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1294b-112">Example</span></span>  

 <span data-ttu-id="1294b-113">O exemplo a seguir mostra como mover arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="1294b-113">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="1294b-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1294b-114">Example</span></span>  

 <span data-ttu-id="1294b-115">O exemplo a seguir mostra como excluir arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="1294b-115">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="1294b-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="1294b-116">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="1294b-117">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="1294b-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1294b-118">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1294b-118">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="1294b-119">Como fornecer uma caixa de diálogo de progresso para operações de arquivo</span><span class="sxs-lookup"><span data-stu-id="1294b-119">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="1294b-120">Arquivo e e/s de fluxo</span><span class="sxs-lookup"><span data-stu-id="1294b-120">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="1294b-121">Tarefas comuns de e/s</span><span class="sxs-lookup"><span data-stu-id="1294b-121">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
