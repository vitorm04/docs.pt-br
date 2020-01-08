---
title: Sistema de arquivos e o Registro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 3e78d49881a4def5fe9c70ecfe890c8ffee811e8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635295"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="067cd-102">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="067cd-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="067cd-103">Os tópicos a seguir mostram como usar o C# e o .NET Framework para executar várias operações básicas em arquivos, pastas e no Registro.</span><span class="sxs-lookup"><span data-stu-id="067cd-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="067cd-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="067cd-104">In This Section</span></span>  
  
|<span data-ttu-id="067cd-105">**Título**</span><span class="sxs-lookup"><span data-stu-id="067cd-105">**Title**</span></span>|<span data-ttu-id="067cd-106">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="067cd-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="067cd-107">Como iterar por meio de uma árvore de diretório</span><span class="sxs-lookup"><span data-stu-id="067cd-107">How to iterate through a directory tree</span></span>](./how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="067cd-108">Mostra como iterar manualmente em uma árvore de diretório.</span><span class="sxs-lookup"><span data-stu-id="067cd-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="067cd-109">Como obter informações sobre arquivos, pastas e unidades</span><span class="sxs-lookup"><span data-stu-id="067cd-109">How to get information about files, folders, and drives</span></span>](./how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="067cd-110">Mostra como recuperar informações como tempo de criação e tamanho, sobre arquivos, pastas e unidades.</span><span class="sxs-lookup"><span data-stu-id="067cd-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="067cd-111">Como criar um arquivo ou uma pasta</span><span class="sxs-lookup"><span data-stu-id="067cd-111">How to create a file or folder</span></span>](./how-to-create-a-file-or-folder.md)|<span data-ttu-id="067cd-112">Mostra como criar um novo arquivo ou pasta.</span><span class="sxs-lookup"><span data-stu-id="067cd-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="067cd-113">Como copiar, excluir e mover arquivos e pastas (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="067cd-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="067cd-114">Mostra como copiar, excluir e mover arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="067cd-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="067cd-115">Como fornecer uma caixa de diálogo de progresso para operações de arquivo</span><span class="sxs-lookup"><span data-stu-id="067cd-115">How to provide a progress dialog box for file operations</span></span>](./how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="067cd-116">Mostra como exibir uma caixa de diálogo de progresso padrão do Windows para determinadas operações de arquivo.</span><span class="sxs-lookup"><span data-stu-id="067cd-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="067cd-117">Como gravar em um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="067cd-117">How to write to a text file</span></span>](./how-to-write-to-a-text-file.md)|<span data-ttu-id="067cd-118">Mostra como gravar em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="067cd-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="067cd-119">Como ler de um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="067cd-119">How to read from a text file</span></span>](./how-to-read-from-a-text-file.md)|<span data-ttu-id="067cd-120">Mostra como ler de um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="067cd-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="067cd-121">Como ler um arquivo de texto uma linha por vez</span><span class="sxs-lookup"><span data-stu-id="067cd-121">How to read a text file one line at a time</span></span>](./how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="067cd-122">Mostra como recuperar o texto do arquivo uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="067cd-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="067cd-123">Como criar uma chave no registro</span><span class="sxs-lookup"><span data-stu-id="067cd-123">How to create a key in the registry</span></span>](./how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="067cd-124">Mostra como gravar uma chave no Registro do sistema.</span><span class="sxs-lookup"><span data-stu-id="067cd-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="067cd-125">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="067cd-125">Related Sections</span></span>  
 [<span data-ttu-id="067cd-126">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="067cd-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="067cd-127">Como copiar, excluir e mover arquivos e pastas (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="067cd-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)
  
 [<span data-ttu-id="067cd-128">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="067cd-128">C# Programming Guide</span></span>](../index.md)  
  
 [<span data-ttu-id="067cd-129">Arquivos, pastas e unidades</span><span class="sxs-lookup"><span data-stu-id="067cd-129">Files, Folders and Drives</span></span>](./index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
