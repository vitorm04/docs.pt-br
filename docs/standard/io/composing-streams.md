---
title: Compondo fluxos
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
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75800210a52620c5b08a01c5f8fa888bf40843fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="composing-streams"></a><span data-ttu-id="bc3cc-102">Compondo fluxos</span><span class="sxs-lookup"><span data-stu-id="bc3cc-102">Composing Streams</span></span>
<span data-ttu-id="bc3cc-103">Um repositório de backup é uma mídia de armazenamento, como um disco ou memória.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="bc3cc-104">Cada armazenamento de backup diferente implementa seu próprio fluxo como uma implementação de <xref:System.IO.Stream> classe.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="bc3cc-105">Cada tipo de fluxo lê e grava bytes de e para seu armazenamento de backup específico.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="bc3cc-106">Fluxos que se conectam aos armazenamentos de backup são chamados fluxos base.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="bc3cc-107">Fluxos base têm construtores que possuem os parâmetros necessários para conectar o fluxo ao armazenamento de backup.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="bc3cc-108">Por exemplo, <xref:System.IO.FileStream> tem construtores que especificam um parâmetro de caminho, que especifica como o arquivo será compartilhado por processos e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="bc3cc-109">O design do <xref:System.IO> classes fornece composição de fluxo simplificada.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="bc3cc-110">Fluxos base podem ser anexados a um ou mais fluxos de passagem que fornecem a funcionalidade desejada.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="bc3cc-111">Um leitor ou gravador pode ser anexado ao final da cadeia de forma que os tipos preferenciais podem ser lidos ou gravados facilmente.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="bc3cc-112">O exemplo de código a seguir cria um **FileStream** em torno de existente `MyFile.txt` em ordem ao buffer `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="bc3cc-113">(Observe que **FileStreams** são armazenados em buffer por padrão.) Em seguida, um <xref:System.IO.StreamReader> é criado para ler caracteres da **FileStream**, que é passado para o **StreamReader** como seu argumento de construtor.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="bc3cc-114"><xref:System.IO.StreamReader.ReadLine%2A>lê até <xref:System.IO.StreamReader.Peek%2A> não localize mais caracteres.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="bc3cc-115">O exemplo de código a seguir cria um **FileStream** em torno de existente `MyFile.txt` em ordem ao buffer `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="bc3cc-116">(Observe que **FileStreams** são armazenados em buffer por padrão.) Em seguida, um **BinaryReader** é criado para ler bytes do **FileStream**, que é passado para o **BinaryReader** como seu argumento de construtor.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="bc3cc-117"><xref:System.IO.BinaryReader.ReadByte%2A>lê até <xref:System.IO.BinaryReader.PeekChar%2A> não localize mais bytes.</span><span class="sxs-lookup"><span data-stu-id="bc3cc-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="bc3cc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc3cc-118">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
