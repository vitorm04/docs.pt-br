---
title: Como ler um arquivo de texto uma linha por vez – guia C# de programação
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: a6af48cdacd836465d776a3fd4e1d17aa0298b77
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635334"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="0b353-102">Como ler um arquivo de texto uma linha de cada vez (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="0b353-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="0b353-103">Este exemplo lê o conteúdo de um arquivo de texto, uma linha por vez, em uma cadeia de caracteres usando o método `ReadLine` da classe `StreamReader`.</span><span class="sxs-lookup"><span data-stu-id="0b353-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="0b353-104">Cada linha de texto é armazenada na cadeia de caracteres `line` e exibida na tela.</span><span class="sxs-lookup"><span data-stu-id="0b353-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b353-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b353-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b353-106">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="0b353-106">Compiling the Code</span></span>  
 <span data-ttu-id="0b353-107">Copie o código e cole-o no método `Main` de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="0b353-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="0b353-108">Substitua `"c:\test.txt"` pelo nome do arquivo real.</span><span class="sxs-lookup"><span data-stu-id="0b353-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0b353-109">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="0b353-109">Robust Programming</span></span>  
 <span data-ttu-id="0b353-110">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="0b353-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0b353-111">O arquivo pode não existir.</span><span class="sxs-lookup"><span data-stu-id="0b353-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0b353-112">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0b353-112">.NET Framework Security</span></span>  
 <span data-ttu-id="0b353-113">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0b353-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="0b353-114">Por exemplo, o arquivo `myFile.cs` pode não ser um arquivo de origem do C#.</span><span class="sxs-lookup"><span data-stu-id="0b353-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b353-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="0b353-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="0b353-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0b353-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0b353-117">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0b353-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
