---
title: "Como ler um arquivo de texto (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2af6102ac6793b4612a6fbc41f8c50189cc24d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="1c70a-102">Como ler um arquivo de texto (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1c70a-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="1c70a-103">Este exemplo lê o conteúdo de um arquivo de texto usando os métodos estáticos <xref:System.IO.File.ReadAllText%2A> e <xref:System.IO.File.ReadAllLines%2A> da classe <xref:System.IO.File?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c70a-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="1c70a-104">Para obter um exemplo que usa o <xref:System.IO.StreamReader>, consulte [Como ler um arquivo de texto uma linha de cada vez](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="1c70a-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c70a-105">Os arquivos usados neste exemplo são criados no tópico [Como gravar em um arquivo de texto](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="1c70a-105">The files that are used in this example are created in the topic [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c70a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c70a-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c70a-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1c70a-107">Compiling the Code</span></span>  
 <span data-ttu-id="1c70a-108">Copie o código e cole-o em um aplicativo de console em C#.</span><span class="sxs-lookup"><span data-stu-id="1c70a-108">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="1c70a-109">Se não estiver usando os arquivos de texto de [Como gravar em um arquivo de texto](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), substitua o argumento de `ReadAllText` e `ReadAllLines` pelo nome de arquivo e pelo caminho adequado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="1c70a-109">If you are not using the text files from [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1c70a-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="1c70a-110">Robust Programming</span></span>  
 <span data-ttu-id="1c70a-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="1c70a-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="1c70a-112">O arquivo não existe ou não existe no local especificado.</span><span class="sxs-lookup"><span data-stu-id="1c70a-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="1c70a-113">Verifique o caminho e a ortografia do nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="1c70a-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1c70a-114">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1c70a-114">.NET Framework Security</span></span>  
 <span data-ttu-id="1c70a-115">Não confie no nome de um arquivo para determinar o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="1c70a-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="1c70a-116">Por exemplo, o arquivo `myFile.cs` pode não ser um arquivo de origem do C#.</span><span class="sxs-lookup"><span data-stu-id="1c70a-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c70a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c70a-117">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="1c70a-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1c70a-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1c70a-119">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1c70a-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
