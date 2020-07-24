---
title: Como combinar consultas LINQ com expressões regulares (C#)
description: Este exemplo cria uma expressão regular para correspondência em cadeias de caracteres de texto usando a classe Regex em C#.
ms.date: 07/20/2015
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
ms.openlocfilehash: af63d096e3c2f19ed557180d82d606989a016120
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105344"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a><span data-ttu-id="b3a37-103">Como combinar consultas LINQ com expressões regulares (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a37-103">How to combine LINQ queries with regular expressions (C#)</span></span>
<span data-ttu-id="b3a37-104">Este exemplo mostra como usar a classe <xref:System.Text.RegularExpressions.Regex> para criar uma expressão regular para correspondências mais complexas em cadeias de texto.</span><span class="sxs-lookup"><span data-stu-id="b3a37-104">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="b3a37-105">A consulta LINQ torna fácil a aplicação de filtro exatamente nos arquivos que você deseja pesquisar com a expressão regular e formatar os resultados.</span><span class="sxs-lookup"><span data-stu-id="b3a37-105">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3a37-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3a37-106">Example</span></span>  
  
```csharp  
class QueryWithRegEx  
{  
    public static void Main()  
    {  
        // Modify this path as necessary so that it accesses your version of Visual Studio.  
        string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio 14.0\";  
        // One of the following paths may be more appropriate on your computer.  
        //string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio\2017\";  
  
        // Take a snapshot of the file system.  
        IEnumerable<System.IO.FileInfo> fileList = GetFiles(startFolder);  
  
        // Create the regular expression to find all things "Visual".  
        System.Text.RegularExpressions.Regex searchTerm =  
            new System.Text.RegularExpressions.Regex(@"Visual (Basic|C#|C\+\+|Studio)");  
  
        // Search the contents of each .htm file.  
        // Remove the where clause to find even more matchedValues!  
        // This query produces a list of files where a match  
        // was found, and a list of the matchedValues in that file.  
        // Note: Explicit typing of "Match" in select clause.  
        // This is required because MatchCollection is not a
        // generic IEnumerable collection.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = System.IO.File.ReadAllText(file.FullName)  
            let matches = searchTerm.Matches(fileText)  
            where matches.Count > 0  
            select new  
            {  
                name = file.FullName,  
                matchedValues = from System.Text.RegularExpressions.Match match in matches  
                                select match.Value  
            };  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm.ToString());  
  
        foreach (var v in queryMatchingFiles)  
        {  
            // Trim the path a bit, then write
            // the file name in which a match was found.  
            string s = v.name.Substring(startFolder.Length - 1);  
            Console.WriteLine(s);  
  
            // For this file, write out all the matching strings  
            foreach (var v2 in v.matchedValues)  
            {  
                Console.WriteLine("  " + v2);  
            }  
        }  
  
        // Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // This method assumes that the application has discovery
    // permissions for all folders under the specified path.  
    static IEnumerable<System.IO.FileInfo> GetFiles(string path)  
    {  
        if (!System.IO.Directory.Exists(path))  
            throw new System.IO.DirectoryNotFoundException();  
  
        string[] fileNames = null;  
        List<System.IO.FileInfo> files = new List<System.IO.FileInfo>();  
  
        fileNames = System.IO.Directory.GetFiles(path, "*.*", System.IO.SearchOption.AllDirectories);  
        foreach (string name in fileNames)  
        {  
            files.Add(new System.IO.FileInfo(name));  
        }  
        return files;  
    }  
}  
```  
  
 <span data-ttu-id="b3a37-107">Observe que também é possível consultar o objeto <xref:System.Text.RegularExpressions.MatchCollection> retornado por uma pesquisa `RegEx`.</span><span class="sxs-lookup"><span data-stu-id="b3a37-107">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="b3a37-108">Neste exemplo, apenas o valor de cada correspondência é produzido nos resultados.</span><span class="sxs-lookup"><span data-stu-id="b3a37-108">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="b3a37-109">No entanto, também é possível usar a LINQ para executar todos os tipos de filtragem, classificação e agrupamento nessa coleção.</span><span class="sxs-lookup"><span data-stu-id="b3a37-109">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="b3a37-110">Como <xref:System.Text.RegularExpressions.MatchCollection> é uma coleção <xref:System.Collections.IEnumerable> não genérica, é necessário declarar explicitamente o tipo da variável de intervalo na consulta.</span><span class="sxs-lookup"><span data-stu-id="b3a37-110">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3a37-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b3a37-111">Compiling the Code</span></span>  
 <span data-ttu-id="b3a37-112">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="b3a37-112">Create a C# console application project with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a37-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3a37-113">See also</span></span>

- [<span data-ttu-id="b3a37-114">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a37-114">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="b3a37-115">LINQ e diretórios de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a37-115">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
