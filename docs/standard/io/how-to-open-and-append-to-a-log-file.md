---
title: Como abrir um arquivo de log e acrescentar dados a ele
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
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="27516-102">Como abrir um arquivo de log e acrescentar dados a ele</span><span class="sxs-lookup"><span data-stu-id="27516-102">How to: Open and Append to a Log File</span></span>
<span data-ttu-id="27516-103"><xref:System.IO.StreamWriter>e <xref:System.IO.StreamReader> gravar caracteres e ler caracteres de fluxos.</span><span class="sxs-lookup"><span data-stu-id="27516-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="27516-104">O código a seguir exemplo abre o `log.txt` do arquivo de entrada, ou cria o arquivo se ele ainda não existir e acrescenta informações ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="27516-104">The following code example opens the `log.txt` file for input, or creates the file if it does not already exist, and appends information to the end of the file.</span></span> <span data-ttu-id="27516-105">O conteúdo do arquivo, em seguida, é gravado para a saída padrão para exibição.</span><span class="sxs-lookup"><span data-stu-id="27516-105">The contents of the file are then written to standard output for display.</span></span> <span data-ttu-id="27516-106">Como alternativa para este exemplo, as informações poderiam ser armazenadas como uma única cadeia de caracteres ou uma matriz de cadeia de caracteres e o <xref:System.IO.File.WriteAllText%2A> ou <xref:System.IO.File.WriteAllLines%2A> método pode ser usado para alcançar a mesma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="27516-106">As an alternative to this example, the information could be stored as a single string or string array, and the <xref:System.IO.File.WriteAllText%2A> or <xref:System.IO.File.WriteAllLines%2A> method could be used to achieve the same functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27516-107">Usuários do Visual Basic podem optar por usar os métodos e propriedades fornecidas pelo <xref:Microsoft.VisualBasic.Logging.Log> classe ou <xref:Microsoft.VisualBasic.FileIO.FileSystem> classe para criar ou gravar em arquivos de log.</span><span class="sxs-lookup"><span data-stu-id="27516-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27516-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27516-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="27516-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27516-109">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="27516-110">Como enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="27516-110">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="27516-111">Como ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="27516-111">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="27516-112">Como ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="27516-112">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="27516-113">Como gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="27516-113">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="27516-114">Como ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="27516-114">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="27516-115">Como gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="27516-115">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="27516-116">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="27516-116">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
