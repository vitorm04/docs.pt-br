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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d49661e93675b80bcd579a6cd341b3dc88a688c2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="composing-streams"></a>Compondo fluxos
Um repositório de backup é uma mídia de armazenamento, como um disco ou memória. Cada repositório de backup diferente implementa seu próprio fluxo como uma implementação da classe <xref:System.IO.Stream>. Cada tipo de fluxo lê e grava bytes de e para seu repositório de backup específico. Os fluxos que se conectam aos repositório de backup são chamados de fluxos base. Os fluxos base têm construtores com os parâmetros necessários para conectar o fluxo ao repositório de backup. Por exemplo, <xref:System.IO.FileStream> tem construtores que especificam um parâmetro de caminho, o qual especifica como o arquivo será compartilhado por processos etc.  
  
 O design das classes <xref:System.IO> fornece composição de fluxo simplificada. Os fluxos base podem ser anexados a um ou mais fluxos de passagem que fornecem a funcionalidade desejada. Um leitor ou gravador pode ser anexado ao final da cadeia, de forma que os tipos preferidos podem ser lidos ou gravados facilmente.  
  
 O exemplo de código a seguir cria um **FileStream** em torno do `MyFile.txt` existente, a fim de armazenar `MyFile.txt` em buffer. (Observe que **FileStreams** são armazenados em buffer por padrão). Em seguida, um <xref:System.IO.StreamReader> é criado para ler caracteres do **FileStream**, que é passado para o **StreamReader** como seu argumento construtor. <xref:System.IO.StreamReader.ReadLine%2A> lê até que <xref:System.IO.StreamReader.Peek%2A> não encontre mais caracteres.  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 O exemplo de código a seguir cria um **FileStream** em torno do `MyFile.txt` existente, a fim de armazenar `MyFile.txt` em buffer. (Observe que **FileStreams** são armazenados em buffer por padrão). Em seguida, um **BinaryReader** é criado para ler caracteres do **FileStream**, que é passado para o **BinaryReader** como seu argumento construtor. <xref:System.IO.BinaryReader.ReadByte%2A> lê até que <xref:System.IO.BinaryReader.PeekChar%2A> não encontre mais bytes.  
  
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
