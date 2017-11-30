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
# <a name="composing-streams"></a>Compondo fluxos
Um repositório de backup é uma mídia de armazenamento, como um disco ou memória. Cada armazenamento de backup diferente implementa seu próprio fluxo como uma implementação de <xref:System.IO.Stream> classe. Cada tipo de fluxo lê e grava bytes de e para seu armazenamento de backup específico. Fluxos que se conectam aos armazenamentos de backup são chamados fluxos base. Fluxos base têm construtores que possuem os parâmetros necessários para conectar o fluxo ao armazenamento de backup. Por exemplo, <xref:System.IO.FileStream> tem construtores que especificam um parâmetro de caminho, que especifica como o arquivo será compartilhado por processos e assim por diante.  
  
 O design do <xref:System.IO> classes fornece composição de fluxo simplificada. Fluxos base podem ser anexados a um ou mais fluxos de passagem que fornecem a funcionalidade desejada. Um leitor ou gravador pode ser anexado ao final da cadeia de forma que os tipos preferenciais podem ser lidos ou gravados facilmente.  
  
 O exemplo de código a seguir cria um **FileStream** em torno de existente `MyFile.txt` em ordem ao buffer `MyFile.txt`. (Observe que **FileStreams** são armazenados em buffer por padrão.) Em seguida, um <xref:System.IO.StreamReader> é criado para ler caracteres da **FileStream**, que é passado para o **StreamReader** como seu argumento de construtor. <xref:System.IO.StreamReader.ReadLine%2A>lê até <xref:System.IO.StreamReader.Peek%2A> não localize mais caracteres.  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 O exemplo de código a seguir cria um **FileStream** em torno de existente `MyFile.txt` em ordem ao buffer `MyFile.txt`. (Observe que **FileStreams** são armazenados em buffer por padrão.) Em seguida, um **BinaryReader** é criado para ler bytes do **FileStream**, que é passado para o **BinaryReader** como seu argumento de construtor. <xref:System.IO.BinaryReader.ReadByte%2A>lê até <xref:System.IO.BinaryReader.PeekChar%2A> não localize mais bytes.  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
