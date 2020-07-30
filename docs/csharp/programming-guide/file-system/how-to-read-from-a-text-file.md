---
title: Como ler de um arquivo de texto – guia de programação C#
description: Saiba como ler de um arquivo de texto usando métodos estáticos da classe File. Consulte um exemplo de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 80ac6f8412f456b23d05ee87882dca8e16a132c3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301652"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="de719-104">Como ler de um arquivo de texto (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="de719-104">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="de719-105">Este exemplo lê o conteúdo de um arquivo de texto usando os métodos estáticos <xref:System.IO.File.ReadAllText%2A> e <xref:System.IO.File.ReadAllLines%2A> da classe <xref:System.IO.File?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de719-105">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="de719-106">Para obter um exemplo que usa <xref:System.IO.StreamReader> , consulte [como ler um arquivo de texto, uma linha por vez](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="de719-106">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="de719-107">Os arquivos usados neste exemplo são criados no tópico [como gravar em um arquivo de texto](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="de719-107">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="de719-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de719-108">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de719-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="de719-109">Compiling the Code</span></span>  
 <span data-ttu-id="de719-110">Copie o código e cole-o em um aplicativo de console em C#.</span><span class="sxs-lookup"><span data-stu-id="de719-110">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="de719-111">Se você não estiver usando os arquivos de texto de [como gravar em um arquivo de texto](./how-to-write-to-a-text-file.md), substitua o argumento para `ReadAllText` e `ReadAllLines` pelo caminho e nome de arquivo apropriados no computador.</span><span class="sxs-lookup"><span data-stu-id="de719-111">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="de719-112">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="de719-112">Robust Programming</span></span>  
 <span data-ttu-id="de719-113">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="de719-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="de719-114">O arquivo não existe ou não existe no local especificado.</span><span class="sxs-lookup"><span data-stu-id="de719-114">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="de719-115">Verifique o caminho e a ortografia do nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="de719-115">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="de719-116">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="de719-116">.NET Security</span></span>  
 <span data-ttu-id="de719-117">Não confie no nome de um arquivo para determinar o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="de719-117">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="de719-118">Por exemplo, o arquivo `myFile.cs` pode não ser um arquivo de origem do C#.</span><span class="sxs-lookup"><span data-stu-id="de719-118">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de719-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="de719-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="de719-120">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="de719-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="de719-121">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="de719-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
