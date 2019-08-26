---
title: 'Como: copiar, excluir e mover arquivos e pastas – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: dd32798062dbfc9a10acd27ce51d8d5dd3b164f6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590093"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="958da-102">Como: copiar, excluir e mover arquivos e pastas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="958da-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="958da-103">Os exemplos a seguir mostram como copiar, mover e excluir arquivos e pastas de maneira síncrona usando as classes <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType> e <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> do namespace <xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="958da-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="958da-104">Esses exemplos não fornecem uma barra de progresso ou qualquer outra interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="958da-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="958da-105">Se você quiser fornecer uma caixa de diálogo de progresso padrão, confira [Como fornecer uma caixa de diálogo de progresso para operações de arquivo](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="958da-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="958da-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> para fornecer eventos que permitirão que você calcule o progresso ao operar em vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="958da-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="958da-107">Outra abordagem é usar a invocação de plataforma para invocar os métodos relacionados ao arquivo relevantes no Shell do Windows.</span><span class="sxs-lookup"><span data-stu-id="958da-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="958da-108">Para obter informações sobre como executar essas operações de arquivo de forma assíncrona, consulte [E/S de arquivo assíncrona](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="958da-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="958da-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="958da-109">Example</span></span>  
 <span data-ttu-id="958da-110">O exemplo a seguir mostra como copiar arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="958da-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="958da-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="958da-111">Example</span></span>  
 <span data-ttu-id="958da-112">O exemplo a seguir mostra como mover arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="958da-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="958da-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="958da-113">Example</span></span>  
 <span data-ttu-id="958da-114">O exemplo a seguir mostra como excluir arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="958da-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="958da-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="958da-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="958da-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="958da-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="958da-117">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="958da-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="958da-118">Como: fornecer uma caixa de diálogo de progresso para operações de arquivo</span><span class="sxs-lookup"><span data-stu-id="958da-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="958da-119">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="958da-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="958da-120">Tarefas comuns de E/S</span><span class="sxs-lookup"><span data-stu-id="958da-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
