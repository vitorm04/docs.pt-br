---
title: Como ler de um guia de C# programação de arquivos de texto
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 4e15d82a303c1a92739c72a2ddffd411debf99d4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635321"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="5128c-102">Como ler de um arquivo de texto (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="5128c-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="5128c-103">Este exemplo lê o conteúdo de um arquivo de texto usando os métodos estáticos <xref:System.IO.File.ReadAllText%2A> e <xref:System.IO.File.ReadAllLines%2A> da classe <xref:System.IO.File?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5128c-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="5128c-104">Para obter um exemplo que usa <xref:System.IO.StreamReader>, consulte [como ler um arquivo de texto, uma linha por vez](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="5128c-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="5128c-105">Os arquivos usados neste exemplo são criados no tópico [como gravar em um arquivo de texto](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="5128c-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="5128c-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5128c-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5128c-107">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="5128c-107">Compiling the Code</span></span>  
 <span data-ttu-id="5128c-108">Copie o código e cole-o em um aplicativo de console em C#.</span><span class="sxs-lookup"><span data-stu-id="5128c-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="5128c-109">Se você não estiver usando os arquivos de texto de [como gravar em um arquivo de texto](./how-to-write-to-a-text-file.md), substitua o argumento para `ReadAllText` e `ReadAllLines` pelo caminho e nome de arquivo apropriados no computador.</span><span class="sxs-lookup"><span data-stu-id="5128c-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="5128c-110">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="5128c-110">Robust Programming</span></span>  
 <span data-ttu-id="5128c-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="5128c-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5128c-112">O arquivo não existe ou não existe no local especificado.</span><span class="sxs-lookup"><span data-stu-id="5128c-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="5128c-113">Verifique o caminho e a ortografia do nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="5128c-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5128c-114">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5128c-114">.NET Framework Security</span></span>  
 <span data-ttu-id="5128c-115">Não confie no nome de um arquivo para determinar o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="5128c-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="5128c-116">Por exemplo, o arquivo `myFile.cs` pode não ser um arquivo de origem do C#.</span><span class="sxs-lookup"><span data-stu-id="5128c-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5128c-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="5128c-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="5128c-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5128c-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5128c-119">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5128c-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
