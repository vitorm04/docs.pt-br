---
title: "Como escrever em um arquivo de texto (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="9b51c-102">Como escrever em um arquivo de texto (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9b51c-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="9b51c-103">Estes exemplos mostram várias maneiras de gravar textos em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="9b51c-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="9b51c-104">Os dois primeiros exemplos usam métodos de conveniência estáticos na classe <xref:System.IO.File?displayProperty=nameWithType> para gravar cada elemento de qualquer IEnumerable\<string> e uma cadeia de caracteres em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="9b51c-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="9b51c-105">O exemplo 3 mostra como adicionar texto a um arquivo quando você precisa processar cada linha individualmente enquanto escreve no arquivo.</span><span class="sxs-lookup"><span data-stu-id="9b51c-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="9b51c-106">Os exemplos de 1 a 3 substituem todo o conteúdo existente no arquivo, mas o exemplo 4 mostra como adicionar texto em um arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="9b51c-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="9b51c-107">Esses exemplos todos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="9b51c-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="9b51c-108">Você também pode usar o recurso [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) do C#.</span><span class="sxs-lookup"><span data-stu-id="9b51c-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b51c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b51c-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 <span data-ttu-id="9b51c-110">Esses exemplos todos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="9b51c-110">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="9b51c-111">Você também pode usar o recurso [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) do C#.</span><span class="sxs-lookup"><span data-stu-id="9b51c-111">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9b51c-112">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="9b51c-112">Robust Programming</span></span>  
 <span data-ttu-id="9b51c-113">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="9b51c-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="9b51c-114">O arquivo existe e é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="9b51c-114">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="9b51c-115">O nome do caminho pode ser muito longo.</span><span class="sxs-lookup"><span data-stu-id="9b51c-115">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="9b51c-116">O disco pode estar cheio.</span><span class="sxs-lookup"><span data-stu-id="9b51c-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b51c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b51c-117">See Also</span></span>  
 [<span data-ttu-id="9b51c-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9b51c-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9b51c-119">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9b51c-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="9b51c-120">Exemplo: salvar uma coleção no armazenamento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="9b51c-120">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
