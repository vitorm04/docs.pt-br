---
title: 'Como: Gravar caracteres em uma cadeia de caracteres'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 125c8ba03c4d1006535dd1e10cbd162b32fede4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740977"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="bb27b-102">Como: Gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bb27b-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="bb27b-103">Os exemplos de código a seguir gravam caracteres de forma síncrona e assíncrona de uma matriz de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bb27b-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb27b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb27b-104">Example</span></span>  
 <span data-ttu-id="bb27b-105">O exemplo a seguir grava cinco caracteres de forma síncrona de uma matriz em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bb27b-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="bb27b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb27b-106">Example</span></span>  
 <span data-ttu-id="bb27b-107">O próximo exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="bb27b-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="bb27b-108">Ele grava de maneira assíncrona cada caractere alfabético ou espaço em branco em uma linha separada, seguida de uma quebra de linha para um controle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="bb27b-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bb27b-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb27b-109">See also</span></span>

- <xref:System.IO.StringWriter>
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="bb27b-110">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="bb27b-110">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="bb27b-111">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="bb27b-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="bb27b-112">Como: Enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="bb27b-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="bb27b-113">Como: Ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="bb27b-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="bb27b-114">Como: Abrir um arquivo de log e fazer acréscimos a ele</span><span class="sxs-lookup"><span data-stu-id="bb27b-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="bb27b-115">Como: Ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="bb27b-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="bb27b-116">Como: Gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="bb27b-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="bb27b-117">Como: Ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bb27b-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
