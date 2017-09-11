---
title: "Sistema de arquivos e o Registro (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6a9130fa666f8b2bce7762c5bd4a8b263d619aba
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="3a375-102">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3a375-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="3a375-103">Os tópicos a seguir mostram como usar o C# e o .NET Framework para executar várias operações básicas em arquivos, pastas e no Registro.</span><span class="sxs-lookup"><span data-stu-id="3a375-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a375-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3a375-104">In This Section</span></span>  
  
|<span data-ttu-id="3a375-105">**Título**</span><span class="sxs-lookup"><span data-stu-id="3a375-105">**Title**</span></span>|<span data-ttu-id="3a375-106">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="3a375-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="3a375-107">Como iterar em uma árvore de diretório</span><span class="sxs-lookup"><span data-stu-id="3a375-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="3a375-108">Mostra como iterar manualmente em uma árvore de diretório.</span><span class="sxs-lookup"><span data-stu-id="3a375-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="3a375-109">Como obter informações sobre arquivos, pastas e unidades</span><span class="sxs-lookup"><span data-stu-id="3a375-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="3a375-110">Mostra como recuperar informações como tempo de criação e tamanho, sobre arquivos, pastas e unidades.</span><span class="sxs-lookup"><span data-stu-id="3a375-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="3a375-111">Como criar um arquivo ou uma pasta</span><span class="sxs-lookup"><span data-stu-id="3a375-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="3a375-112">Mostra como criar um novo arquivo ou pasta.</span><span class="sxs-lookup"><span data-stu-id="3a375-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="3a375-113">Como copiar, excluir e mover arquivos e pastas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3a375-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="3a375-114">Mostra como copiar, excluir e mover arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="3a375-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="3a375-115">Como fornecer uma caixa de diálogo de progresso para operações de arquivo</span><span class="sxs-lookup"><span data-stu-id="3a375-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="3a375-116">Mostra como exibir uma caixa de diálogo de progresso padrão do Windows para determinadas operações de arquivo.</span><span class="sxs-lookup"><span data-stu-id="3a375-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="3a375-117">Como gravar em um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="3a375-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="3a375-118">Mostra como gravar em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="3a375-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="3a375-119">Como ler de um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="3a375-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="3a375-120">Mostra como ler de um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="3a375-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="3a375-121">Como ler um arquivo de texto uma linha de cada vez</span><span class="sxs-lookup"><span data-stu-id="3a375-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="3a375-122">Mostra como recuperar o texto do arquivo uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="3a375-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="3a375-123">Como criar uma chave no Registro</span><span class="sxs-lookup"><span data-stu-id="3a375-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="3a375-124">Mostra como gravar uma chave no Registro do sistema.</span><span class="sxs-lookup"><span data-stu-id="3a375-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="3a375-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="3a375-125">Related Sections</span></span>  
 [<span data-ttu-id="3a375-126">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="3a375-126">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
  
 [<span data-ttu-id="3a375-127">Como copiar, excluir e mover arquivos e pastas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3a375-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="3a375-128">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3a375-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="3a375-129">Arquivos, pastas e unidades</span><span class="sxs-lookup"><span data-stu-id="3a375-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=fullName>

