---
title: 'Como: escrever em um arquivo de texto – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: da1526afe48a0d4bda63274380dcf59ee30c480e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968792"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="fdc9f-102">Como: escrever em um arquivo de texto (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fdc9f-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="fdc9f-103">Estes exemplos mostram várias maneiras de gravar textos em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="fdc9f-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="fdc9f-104">Os dois primeiros exemplos usam métodos de conveniência estáticos na classe <xref:System.IO.File?displayProperty=nameWithType> para gravar cada elemento de qualquer `IEnumerable<string>` e uma cadeia de caracteres em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="fdc9f-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="fdc9f-105">O exemplo 3 mostra como adicionar texto a um arquivo quando você precisa processar cada linha individualmente enquanto escreve no arquivo.</span><span class="sxs-lookup"><span data-stu-id="fdc9f-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="fdc9f-106">Os exemplos de 1 a 3 substituem todo o conteúdo existente no arquivo, mas o exemplo 4 mostra como adicionar texto em um arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="fdc9f-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="fdc9f-107">Todos esses exemplos gravam literais de cadeia de caracteres em arquivos.</span><span class="sxs-lookup"><span data-stu-id="fdc9f-107">These examples all write string literals to files.</span></span> <span data-ttu-id="fdc9f-108">Se você quiser formatar o texto gravado em um arquivo, use o método <xref:System.String.Format%2A> ou o recurso de [interpolação de cadeia de caracteres](../../../csharp/language-reference/tokens/interpolated.md) do C#.</span><span class="sxs-lookup"><span data-stu-id="fdc9f-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../../csharp/language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdc9f-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fdc9f-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fdc9f-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fdc9f-110">Robust Programming</span></span>  
 <span data-ttu-id="fdc9f-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="fdc9f-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="fdc9f-112">O arquivo existe e é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="fdc9f-112">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="fdc9f-113">O nome do caminho pode ser muito longo.</span><span class="sxs-lookup"><span data-stu-id="fdc9f-113">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="fdc9f-114">O disco pode estar cheio.</span><span class="sxs-lookup"><span data-stu-id="fdc9f-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc9f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdc9f-115">See also</span></span>

- [<span data-ttu-id="fdc9f-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fdc9f-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fdc9f-117">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fdc9f-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
- [<span data-ttu-id="fdc9f-118">Exemplo: salvar uma coleção no armazenamento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="fdc9f-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
