---
title: Como escrever em um guia de programação de C# arquivos de texto
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: c0b6646e0d7f453dc9021a7470a3671f11ea0653
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635412"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="5cd34-102">Como gravar em um arquivo de texto (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="5cd34-102">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="5cd34-103">Estes exemplos mostram várias maneiras de gravar textos em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="5cd34-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="5cd34-104">Os dois primeiros exemplos usam métodos de conveniência estáticos na classe <xref:System.IO.File?displayProperty=nameWithType> para gravar cada elemento de qualquer `IEnumerable<string>` e uma cadeia de caracteres em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="5cd34-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="5cd34-105">O exemplo 3 mostra como adicionar texto a um arquivo quando você precisa processar cada linha individualmente enquanto escreve no arquivo.</span><span class="sxs-lookup"><span data-stu-id="5cd34-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="5cd34-106">Os exemplos de 1 a 3 substituem todo o conteúdo existente no arquivo, mas o exemplo 4 mostra como adicionar texto em um arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="5cd34-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="5cd34-107">Todos esses exemplos gravam literais de cadeia de caracteres em arquivos.</span><span class="sxs-lookup"><span data-stu-id="5cd34-107">These examples all write string literals to files.</span></span> <span data-ttu-id="5cd34-108">Se você quiser formatar o texto gravado em um arquivo, use o método <xref:System.String.Format%2A> ou o recurso de [interpolação de cadeia de caracteres](../../language-reference/tokens/interpolated.md) do C#.</span><span class="sxs-lookup"><span data-stu-id="5cd34-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cd34-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5cd34-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5cd34-110">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="5cd34-110">Robust Programming</span></span>  
 <span data-ttu-id="5cd34-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="5cd34-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5cd34-112">O arquivo existe e é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="5cd34-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="5cd34-113">O nome do caminho pode ser muito longo.</span><span class="sxs-lookup"><span data-stu-id="5cd34-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="5cd34-114">O disco pode estar cheio.</span><span class="sxs-lookup"><span data-stu-id="5cd34-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd34-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="5cd34-115">See also</span></span>

- [<span data-ttu-id="5cd34-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5cd34-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5cd34-117">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5cd34-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="5cd34-118">Exemplo: salvar uma coleção no armazenamento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="5cd34-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
