---
title: 'Como: Escrever caracteres em uma seqüência'
ms.date: 01/21/2019
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
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160268"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="8e312-102">Como: Escrever caracteres em uma seqüência</span><span class="sxs-lookup"><span data-stu-id="8e312-102">How to: Write characters to a string</span></span>
<span data-ttu-id="8e312-103">Os exemplos de código a seguir gravam caracteres de forma síncrona ou assíncrona de uma matriz de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8e312-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="8e312-104">Exemplo: Escreva caracteres sincronizadamente em um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="8e312-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="8e312-105">O exemplo a seguir usa um <xref:System.IO.StringWriter> para gravar cinco caracteres de forma síncrona em um objeto <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="8e312-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="8e312-106">Exemplo: Escreva caracteres assíncronamente em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="8e312-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="8e312-107">O próximo exemplo é o código por trás de um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="8e312-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="8e312-108">Na carga de janela, o exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="8e312-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="8e312-109">Em seguida, ele grava cada letra ou caractere de espaço em branco de forma assíncrona em uma linha separada de um controle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="8e312-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8e312-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="8e312-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="8e312-111">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="8e312-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="8e312-112">I/O do arquivo assíncrono</span><span class="sxs-lookup"><span data-stu-id="8e312-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="8e312-113">Como: Enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="8e312-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="8e312-114">Como: Ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="8e312-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="8e312-115">Como: Abrir e anexar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="8e312-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="8e312-116">Como: Ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="8e312-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="8e312-117">Como: Escrever texto para um arquivo</span><span class="sxs-lookup"><span data-stu-id="8e312-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="8e312-118">Como: Ler caracteres de uma seqüência</span><span class="sxs-lookup"><span data-stu-id="8e312-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
