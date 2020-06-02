---
title: 'Como: gravar caracteres em uma cadeia de caracteres'
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
ms.openlocfilehash: 04fc21c452258a88292a886d952353ac55573121
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288245"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="9588a-102">Como: gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9588a-102">How to: Write characters to a string</span></span>
<span data-ttu-id="9588a-103">Os exemplos de código a seguir gravam caracteres de forma síncrona ou assíncrona de uma matriz de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9588a-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="9588a-104">Exemplo: gravar caracteres de forma síncrona em um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="9588a-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="9588a-105">O exemplo a seguir usa um <xref:System.IO.StringWriter> para gravar cinco caracteres de forma síncrona em um objeto <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="9588a-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="9588a-106">Exemplo: gravar caracteres de forma assíncrona em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="9588a-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="9588a-107">O próximo exemplo é o código por trás de um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="9588a-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="9588a-108">Na carga de janela, o exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="9588a-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="9588a-109">Em seguida, ele grava cada letra ou caractere de espaço em branco de forma assíncrona em uma linha separada de um controle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="9588a-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9588a-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="9588a-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="9588a-111">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="9588a-111">File and stream I/O</span></span>](index.md)  
- [<span data-ttu-id="9588a-112">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="9588a-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- [<span data-ttu-id="9588a-113">Como: enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="9588a-113">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="9588a-114">Como: ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="9588a-114">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="9588a-115">Como: abrir e anexar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="9588a-115">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="9588a-116">Como: ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="9588a-116">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="9588a-117">Como: gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="9588a-117">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="9588a-118">Como: ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9588a-118">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)
