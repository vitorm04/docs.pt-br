---
title: 'Como: Escrever texto para um arquivo'
ms.date: 01/04/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
ms.openlocfilehash: ba1c1815f0e49c02d1f0ee3c48ba01b7c2f5e727
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160242"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="4fea7-102">Como: Escrever texto para um arquivo</span><span class="sxs-lookup"><span data-stu-id="4fea7-102">How to: Write text to a file</span></span>
<span data-ttu-id="4fea7-103">Este tópico mostra diferentes maneiras de gravar um texto em um arquivo para um aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="4fea7-103">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="4fea7-104">As classes e métodos seguintes normalmente são usados para gravar texto em um arquivo:</span><span class="sxs-lookup"><span data-stu-id="4fea7-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="4fea7-105"><xref:System.IO.StreamWriter> contém métodos para gravação síncrona (<xref:System.IO.StreamWriter.Write%2A> ou <xref:System.IO.TextWriter.WriteLine%2A>) ou assíncrona (<xref:System.IO.StreamWriter.WriteAsync%2A> e <xref:System.IO.StreamWriter.WriteLineAsync%2A>) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="4fea7-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="4fea7-106"><xref:System.IO.File> fornece métodos estáticos para gravar um texto em um arquivo, como <xref:System.IO.File.WriteAllLines%2A> e <xref:System.IO.File.WriteAllText%2A>, ou para acrescentar um texto a um arquivo, como <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> e <xref:System.IO.File.AppendText%2A>.</span><span class="sxs-lookup"><span data-stu-id="4fea7-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="4fea7-107"><xref:System.IO.Path> destina-se a cadeias de caracteres que contêm informações de caminho de arquivo ou diretório.</span><span class="sxs-lookup"><span data-stu-id="4fea7-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="4fea7-108">Ele contém o método <xref:System.IO.Path.Combine%2A> e, no .NET Core 2.1 e posterior, os métodos <xref:System.IO.Path.Join%2A> e <xref:System.IO.Path.TryJoin%2A>, que permitem que a concatenação de cadeias de caracteres crie um caminho de arquivo ou diretório.</span><span class="sxs-lookup"><span data-stu-id="4fea7-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="4fea7-109">Os exemplos a seguir mostram apenas a quantidade mínima de código necessário.</span><span class="sxs-lookup"><span data-stu-id="4fea7-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="4fea7-110">Um aplicativo do mundo real geralmente fornece verificação de erros e tratamento de exceção mais robustos.</span><span class="sxs-lookup"><span data-stu-id="4fea7-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="4fea7-111">Exemplo: Escreva texto sincronicamente com streamwriter</span><span class="sxs-lookup"><span data-stu-id="4fea7-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="4fea7-112">O exemplo a seguir mostra como usar a classe <xref:System.IO.StreamWriter> para gravar um texto de forma síncrona em um novo arquivo, uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="4fea7-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="4fea7-113">Como o objeto <xref:System.IO.StreamWriter> é declarado e instanciado em uma instrução `using`, o método <xref:System.IO.StreamWriter.Dispose%2A> é invocado, o que libera e fecha o fluxo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4fea7-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="4fea7-114">Exemplo: Texto de apêndice sincronicamente com StreamWriter</span><span class="sxs-lookup"><span data-stu-id="4fea7-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="4fea7-115">O exemplo a seguir mostra como usar a classe <xref:System.IO.StreamWriter> para acrescentar um texto de forma síncrona ao arquivo de texto criado no primeiro exemplo.</span><span class="sxs-lookup"><span data-stu-id="4fea7-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="4fea7-116">Exemplo: Escreva texto assíncronamente com streamwriter</span><span class="sxs-lookup"><span data-stu-id="4fea7-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="4fea7-117">O exemplo a seguir mostra como gravar texto de maneira assíncrona em um novo arquivo usando a classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="4fea7-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="4fea7-118">Para invocar o método <xref:System.IO.StreamWriter.WriteAsync%2A>, a chamada de método precisa estar dentro de um método `async`.</span><span class="sxs-lookup"><span data-stu-id="4fea7-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="4fea7-119">O exemplo em C# exige o C# 7.1 ou posterior, o que adiciona suporte ao modificador `async` no ponto de entrada do programa.</span><span class="sxs-lookup"><span data-stu-id="4fea7-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="4fea7-120">Exemplo: Escreva e apêndice texto com a classe Arquivo</span><span class="sxs-lookup"><span data-stu-id="4fea7-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="4fea7-121">O exemplo a seguir mostra como gravar texto em um novo arquivo e acrescentar novas linhas de texto ao mesmo arquivo usando a classe <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="4fea7-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="4fea7-122">Os métodos <xref:System.IO.File.WriteAllText%2A> e <xref:System.IO.File.AppendAllLines%2A> abrem e fecham o arquivo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4fea7-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="4fea7-123">Se o caminho que você fornecer ao método <xref:System.IO.File.WriteAllText%2A> já existir, o arquivo será substituído.</span><span class="sxs-lookup"><span data-stu-id="4fea7-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="4fea7-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="4fea7-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4fea7-125">Como: Enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="4fea7-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="4fea7-126">Como: Ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="4fea7-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="4fea7-127">Como: Abrir e anexar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="4fea7-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="4fea7-128">Como: Ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="4fea7-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="4fea7-129">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="4fea7-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
