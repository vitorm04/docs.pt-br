---
title: "Como escrever em um arquivo de texto (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
dev_langs:
- CSharp
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 12a74a5664a8f514c89d9de3ce470c98319f84d2
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="db28a-102">Como escrever em um arquivo de texto (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="db28a-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="db28a-103">Estes exemplos mostram várias maneiras de gravar textos em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="db28a-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="db28a-104">Os dois primeiros exemplos usam métodos de conveniência estáticos na classe <xref:System.IO.File?displayProperty=fullName> para gravar cada elemento de qualquer IEnumerable\<string> e uma cadeia de caracteres em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="db28a-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=fullName> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="db28a-105">O exemplo 3 mostra como adicionar texto a um arquivo quando você precisa processar cada linha individualmente enquanto escreve no arquivo.</span><span class="sxs-lookup"><span data-stu-id="db28a-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="db28a-106">Os exemplos de 1 a 3 substituem todo o conteúdo existente no arquivo, mas o exemplo 4 mostra como adicionar texto em um arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="db28a-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="db28a-107">Esses exemplos todos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="db28a-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="db28a-108">Você também pode usar o recurso [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) do C#.</span><span class="sxs-lookup"><span data-stu-id="db28a-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db28a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db28a-109">Example</span></span>  
 <span data-ttu-id="db28a-110">[!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="db28a-110">[!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]</span></span>  
  
 <span data-ttu-id="db28a-111">Esses exemplos todos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="db28a-111">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="db28a-112">Você também pode usar o recurso [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) do C#.</span><span class="sxs-lookup"><span data-stu-id="db28a-112">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="db28a-113">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="db28a-113">Robust Programming</span></span>  
 <span data-ttu-id="db28a-114">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="db28a-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="db28a-115">O arquivo existe e é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="db28a-115">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="db28a-116">O nome do caminho pode ser muito longo.</span><span class="sxs-lookup"><span data-stu-id="db28a-116">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="db28a-117">O disco pode estar cheio.</span><span class="sxs-lookup"><span data-stu-id="db28a-117">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db28a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db28a-118">See Also</span></span>  
 <span data-ttu-id="db28a-119">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="db28a-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="db28a-120">[Sistema de arquivos e o Registro (Guia de Programação em C#)](../../../csharp/programming-guide/file-system/index.md) </span><span class="sxs-lookup"><span data-stu-id="db28a-120">[File System and the Registry (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md) </span></span>  
 [<span data-ttu-id="db28a-121">Exemplo: salvar uma coleção no armazenamento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="db28a-121">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)

