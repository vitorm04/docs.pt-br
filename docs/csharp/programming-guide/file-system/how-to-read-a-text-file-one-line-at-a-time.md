---
title: Como ler um arquivo de texto uma linha de cada vez (Visual C#)
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 2ed0069f9313955edc2cc46ecfd395a5f1ac2852
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339729"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="6ca02-102">Como ler um arquivo de texto uma linha de cada vez (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="6ca02-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="6ca02-103">Este exemplo lê o conteúdo de um arquivo de texto, uma linha por vez, em uma cadeia de caracteres usando o método `ReadLine` da classe `StreamReader`.</span><span class="sxs-lookup"><span data-stu-id="6ca02-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="6ca02-104">Cada linha de texto é armazenada na cadeia de caracteres `line` e exibida na tela.</span><span class="sxs-lookup"><span data-stu-id="6ca02-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ca02-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ca02-105">Example</span></span>  
  
```  
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine (line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6ca02-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6ca02-106">Compiling the Code</span></span>  
 <span data-ttu-id="6ca02-107">Copie o código e cole-o no método `Main` de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="6ca02-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="6ca02-108">Substitua `"c:\test.txt"` pelo nome do arquivo real.</span><span class="sxs-lookup"><span data-stu-id="6ca02-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6ca02-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="6ca02-109">Robust Programming</span></span>  
 <span data-ttu-id="6ca02-110">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="6ca02-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6ca02-111">O arquivo pode não existir.</span><span class="sxs-lookup"><span data-stu-id="6ca02-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6ca02-112">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6ca02-112">.NET Framework Security</span></span>  
 <span data-ttu-id="6ca02-113">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6ca02-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="6ca02-114">Por exemplo, o arquivo `myFile.cs` pode não ser um arquivo de origem do C#.</span><span class="sxs-lookup"><span data-stu-id="6ca02-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca02-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ca02-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="6ca02-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6ca02-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6ca02-117">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="6ca02-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
