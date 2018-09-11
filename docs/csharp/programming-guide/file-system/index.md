---
title: Sistema de arquivos e o Registro (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 3625f7a108675a3a9ab6be16ef94ae7e7c107612
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368972"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="52876-102">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="52876-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="52876-103">Os tópicos a seguir mostram como usar o C# e o .NET Framework para executar várias operações básicas em arquivos, pastas e no Registro.</span><span class="sxs-lookup"><span data-stu-id="52876-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52876-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="52876-104">In This Section</span></span>  
  
|<span data-ttu-id="52876-105">**Título**</span><span class="sxs-lookup"><span data-stu-id="52876-105">**Title**</span></span>|<span data-ttu-id="52876-106">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="52876-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="52876-107">Como iterar em uma árvore de diretório</span><span class="sxs-lookup"><span data-stu-id="52876-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="52876-108">Mostra como iterar manualmente em uma árvore de diretório.</span><span class="sxs-lookup"><span data-stu-id="52876-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="52876-109">Como obter informações sobre arquivos, pastas e unidades</span><span class="sxs-lookup"><span data-stu-id="52876-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="52876-110">Mostra como recuperar informações como tempo de criação e tamanho, sobre arquivos, pastas e unidades.</span><span class="sxs-lookup"><span data-stu-id="52876-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="52876-111">Como criar um arquivo ou uma pasta</span><span class="sxs-lookup"><span data-stu-id="52876-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="52876-112">Mostra como criar um novo arquivo ou pasta.</span><span class="sxs-lookup"><span data-stu-id="52876-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="52876-113">Como copiar, excluir e mover arquivos e pastas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="52876-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="52876-114">Mostra como copiar, excluir e mover arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="52876-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="52876-115">Como fornecer uma caixa de diálogo de progresso para operações de arquivo</span><span class="sxs-lookup"><span data-stu-id="52876-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="52876-116">Mostra como exibir uma caixa de diálogo de progresso padrão do Windows para determinadas operações de arquivo.</span><span class="sxs-lookup"><span data-stu-id="52876-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="52876-117">Como gravar em um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="52876-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="52876-118">Mostra como gravar em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="52876-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="52876-119">Como ler de um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="52876-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="52876-120">Mostra como ler de um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="52876-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="52876-121">Como ler um arquivo de texto uma linha de cada vez</span><span class="sxs-lookup"><span data-stu-id="52876-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="52876-122">Mostra como recuperar o texto do arquivo uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="52876-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="52876-123">Como criar uma chave no Registro</span><span class="sxs-lookup"><span data-stu-id="52876-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="52876-124">Mostra como gravar uma chave no Registro do sistema.</span><span class="sxs-lookup"><span data-stu-id="52876-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="52876-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="52876-125">Related Sections</span></span>  
 [<span data-ttu-id="52876-126">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="52876-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="52876-127">Como copiar, excluir e mover arquivos e pastas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="52876-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="52876-128">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="52876-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="52876-129">Arquivos, pastas e unidades</span><span class="sxs-lookup"><span data-stu-id="52876-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
