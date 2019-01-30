---
title: 'Como: Agrupar arquivos por extensão (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: bad4df9009a40cede04438063b2d30916d0e68b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575142"
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="95527-102">Como: Agrupar arquivos por extensão (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="95527-102">How to: Group Files by Extension (LINQ) (C#)</span></span>
<span data-ttu-id="95527-103">Este exemplo mostra como o LINQ pode ser usado para realizar operações avançadas de classificação e agrupamento em listas de arquivos ou pastas.</span><span class="sxs-lookup"><span data-stu-id="95527-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="95527-104">Ele também mostra como paginar a saída na janela do console usando os métodos <xref:System.Linq.Enumerable.Skip%2A> e <xref:System.Linq.Enumerable.Take%2A>.</span><span class="sxs-lookup"><span data-stu-id="95527-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95527-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95527-105">Example</span></span>  
 <span data-ttu-id="95527-106">A consulta a seguir mostra como agrupar o conteúdo de uma árvore de diretórios especificada, pela extensão de nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="95527-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of   
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="95527-107">A saída desse programa pode ser longa, dependendo dos detalhes do sistema de arquivos local e o que está definido em `startFolder`.</span><span class="sxs-lookup"><span data-stu-id="95527-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="95527-108">Para habilitar a exibição de todos os resultados, este exemplo mostra como paginá-los.</span><span class="sxs-lookup"><span data-stu-id="95527-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="95527-109">As mesmas técnicas podem ser aplicadas a aplicativos do Windows e aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="95527-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="95527-110">Observe que, como o código dispõe os itens em um grupo, é necessário um loop `foreach` aninhado.</span><span class="sxs-lookup"><span data-stu-id="95527-110">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="95527-111">Há também alguma lógica adicional para calcular a posição atual na lista e para permitir que o usuário interrompa a paginação e saia do programa.</span><span class="sxs-lookup"><span data-stu-id="95527-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="95527-112">Nesse caso específico, a consulta de paginação é executada nos resultados da consulta original armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="95527-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="95527-113">Em outros contextos, como LINQ to SQL, esse cache não é necessário.</span><span class="sxs-lookup"><span data-stu-id="95527-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95527-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="95527-114">Compiling the Code</span></span>  
 <span data-ttu-id="95527-115">Crie um projeto que tenha como alvo o .NET Framework versão 3.5 ou posterior, com uma referência a System.Core.dll e diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="95527-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95527-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95527-116">See also</span></span>

- [<span data-ttu-id="95527-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="95527-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="95527-118">LINQ e diretórios de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="95527-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
