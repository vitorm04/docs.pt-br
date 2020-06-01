---
title: Como ler um arquivo de texto de uma linha por vez – guia de programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b54d072ce9837f9b15694f2d7100817de62e9762
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241767"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="632af-102">Como ler um arquivo de texto uma linha de cada vez (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="632af-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="632af-103">Este exemplo lê o conteúdo de um arquivo de texto, uma linha por vez, em uma cadeia de caracteres usando o método `ReadLine` da classe `StreamReader`.</span><span class="sxs-lookup"><span data-stu-id="632af-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="632af-104">Cada linha de texto é armazenada na cadeia de caracteres `line` e exibida na tela.</span><span class="sxs-lookup"><span data-stu-id="632af-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="632af-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="632af-105">Example</span></span>  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="632af-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="632af-106">Compiling the Code</span></span>  
 <span data-ttu-id="632af-107">Copie o código e cole-o no método `Main` de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="632af-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="632af-108">Substitua `"c:\test.txt"` pelo nome do arquivo real.</span><span class="sxs-lookup"><span data-stu-id="632af-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="632af-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="632af-109">Robust Programming</span></span>  
 <span data-ttu-id="632af-110">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="632af-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="632af-111">O arquivo pode não existir.</span><span class="sxs-lookup"><span data-stu-id="632af-111">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="632af-112">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="632af-112">.NET Security</span></span>  
 <span data-ttu-id="632af-113">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="632af-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="632af-114">Por exemplo, o arquivo `myFile.cs` pode não ser um arquivo de origem do C#.</span><span class="sxs-lookup"><span data-stu-id="632af-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="632af-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="632af-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="632af-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="632af-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="632af-117">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="632af-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
