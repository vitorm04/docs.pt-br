---
title: Como escrever caracteres em uma cadeia de caracteres
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
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d409b9f9cada319c64c4b5a1315b8a5abbd731e9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="bd9fd-102">Como escrever caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bd9fd-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="bd9fd-103">Os exemplos de código a seguir gravam caracteres de forma síncrona e assíncrona de uma matriz de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd9fd-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd9fd-104">Example</span></span>  
 <span data-ttu-id="bd9fd-105">O exemplo a seguir grava cinco caracteres de forma síncrona de uma matriz em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="bd9fd-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd9fd-106">Example</span></span>  
 <span data-ttu-id="bd9fd-107">O próximo exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="bd9fd-108">Ele grava de maneira assíncrona cada caractere alfabético ou espaço em branco em uma linha separada, seguida de uma quebra de linha para um controle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bd9fd-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd9fd-109">See Also</span></span>  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="bd9fd-110">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="bd9fd-110">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="bd9fd-111">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="bd9fd-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="bd9fd-112">Como enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="bd9fd-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="bd9fd-113">Como ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="bd9fd-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="bd9fd-114">Como abrir e acrescentar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="bd9fd-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="bd9fd-115">Como ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="bd9fd-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="bd9fd-116">Como gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="bd9fd-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="bd9fd-117">Como ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bd9fd-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
