---
title: Compondo fluxos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e52b827f337892c33ec61b9affa1cc646a759c5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44182458"
---
# <a name="composing-streams"></a><span data-ttu-id="95694-102">Compondo fluxos</span><span class="sxs-lookup"><span data-stu-id="95694-102">Composing Streams</span></span>
<span data-ttu-id="95694-103">Um repositório de backup é uma mídia de armazenamento, como um disco ou memória.</span><span class="sxs-lookup"><span data-stu-id="95694-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="95694-104">Cada repositório de backup diferente implementa seu próprio fluxo como uma implementação da classe <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="95694-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="95694-105">Cada tipo de fluxo lê e grava bytes de e para seu repositório de backup específico.</span><span class="sxs-lookup"><span data-stu-id="95694-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="95694-106">Os fluxos que se conectam aos repositório de backup são chamados de fluxos base.</span><span class="sxs-lookup"><span data-stu-id="95694-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="95694-107">Os fluxos base têm construtores com os parâmetros necessários para conectar o fluxo ao repositório de backup.</span><span class="sxs-lookup"><span data-stu-id="95694-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="95694-108">Por exemplo, <xref:System.IO.FileStream> tem construtores que especificam um parâmetro de caminho, o qual especifica como o arquivo será compartilhado por processos etc.</span><span class="sxs-lookup"><span data-stu-id="95694-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="95694-109">O design das classes <xref:System.IO> fornece composição de fluxo simplificada.</span><span class="sxs-lookup"><span data-stu-id="95694-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="95694-110">Os fluxos base podem ser anexados a um ou mais fluxos de passagem que fornecem a funcionalidade desejada.</span><span class="sxs-lookup"><span data-stu-id="95694-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="95694-111">Um leitor ou gravador pode ser anexado ao final da cadeia, de forma que os tipos preferidos podem ser lidos ou gravados facilmente.</span><span class="sxs-lookup"><span data-stu-id="95694-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="95694-112">O exemplo de código a seguir cria um **FileStream** em torno do `MyFile.txt` existente, a fim de armazenar `MyFile.txt` em buffer.</span><span class="sxs-lookup"><span data-stu-id="95694-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="95694-113">(Observe que **FileStreams** são armazenados em buffer por padrão). Em seguida, um <xref:System.IO.StreamReader> é criado para ler caracteres do **FileStream**, que é passado para o **StreamReader** como seu argumento construtor.</span><span class="sxs-lookup"><span data-stu-id="95694-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="95694-114"><xref:System.IO.StreamReader.ReadLine%2A> lê até que <xref:System.IO.StreamReader.Peek%2A> não encontre mais caracteres.</span><span class="sxs-lookup"><span data-stu-id="95694-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="95694-115">O exemplo de código a seguir cria um **FileStream** em torno do `MyFile.txt` existente, a fim de armazenar `MyFile.txt` em buffer.</span><span class="sxs-lookup"><span data-stu-id="95694-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="95694-116">(Observe que **FileStreams** são armazenados em buffer por padrão). Em seguida, um **BinaryReader** é criado para ler caracteres do **FileStream**, que é passado para o **BinaryReader** como seu argumento construtor.</span><span class="sxs-lookup"><span data-stu-id="95694-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="95694-117"><xref:System.IO.BinaryReader.ReadByte%2A> lê até que <xref:System.IO.BinaryReader.PeekChar%2A> não encontre mais bytes.</span><span class="sxs-lookup"><span data-stu-id="95694-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="95694-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95694-118">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
