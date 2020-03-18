---
title: Como consultar o conteúdo de arquivos de texto em uma pasta (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 998fddd3f59ee64df9adcee1acc720d82861c3d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168733"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="0dcd5-102">Como consultar o conteúdo de arquivos de texto em uma pasta (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0dcd5-102">How to query the contents of text files in a folder (LINQ) (C#)</span></span>
<span data-ttu-id="0dcd5-103">Este exemplo mostra como consultar todos os arquivos em uma árvore de diretório especificada, abrir cada arquivo e inspecionar seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0dcd5-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="0dcd5-104">Este tipo de técnica pode ser usado para criar índices ou inverter os índices do conteúdo de uma árvore de diretório.</span><span class="sxs-lookup"><span data-stu-id="0dcd5-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="0dcd5-105">Uma pesquisa de cadeia de caracteres simples é executada neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="0dcd5-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="0dcd5-106">No entanto, os tipos de correspondência de padrões mais complexos podem ser executados com uma expressão regular.</span><span class="sxs-lookup"><span data-stu-id="0dcd5-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="0dcd5-107">Para obter mais informações, consulte [Como combinar consultas LINQ com expressões regulares (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0dcd5-107">For more information, see [How to combine LINQ queries with regular expressions (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dcd5-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0dcd5-108">Example</span></span>  
  
```csharp  
class QueryContents  
{  
    public static void Main()  
    {  
        // Modify this path as necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        string searchTerm = @"Visual Studio";  
  
        // Search the contents of each file.  
        // A regular expression created with the RegEx class  
        // could be used instead of the Contains method.  
        // queryMatchingFiles is an IEnumerable<string>.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = GetFileText(file.FullName)  
            where fileText.Contains(searchTerm)  
            select file.FullName;  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm);  
        foreach (string filename in queryMatchingFiles)  
        {  
            Console.WriteLine(filename);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Read the contents of the file.  
    static string GetFileText(string name)  
    {  
        string fileContents = String.Empty;  
  
        // If the file has been deleted since we took
        // the snapshot, ignore it and return the empty string.  
        if (System.IO.File.Exists(name))  
        {  
            fileContents = System.IO.File.ReadAllText(name);  
        }  
        return fileContents;  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0dcd5-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0dcd5-109">Compiling the Code</span></span>  
<span data-ttu-id="0dcd5-110">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="0dcd5-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0dcd5-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="0dcd5-111">See also</span></span>

- [<span data-ttu-id="0dcd5-112">LINQ e diretórios de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="0dcd5-112">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="0dcd5-113">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="0dcd5-113">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
