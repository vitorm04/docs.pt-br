---
title: 'Como: Consultar arquivos com um atributo ou um nome especificado (C#)'
ms.date: 07/20/2015
ms.assetid: 560e3879-b0b3-4549-ad02-0a53aff2f83c
ms.openlocfilehash: c1ecaad7e4fb4538331ba8f8076c9795acc52877
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592905"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-c"></a><span data-ttu-id="9251e-102">Como: Consultar arquivos com um atributo ou um nome especificado (C#)</span><span class="sxs-lookup"><span data-stu-id="9251e-102">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>
<span data-ttu-id="9251e-103">Este exemplo mostra como localizar todos os arquivos que têm uma extensão de nome de arquivo especificada (por exemplo ".txt") em uma árvore de diretório especificada.</span><span class="sxs-lookup"><span data-stu-id="9251e-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="9251e-104">Ele também mostra como retornar tanto os arquivos mais recentes como os mais antigo na árvore com base na hora de criação.</span><span class="sxs-lookup"><span data-stu-id="9251e-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9251e-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9251e-105">Example</span></span>  
  
```csharp  
class FindFileByExtension  
{  
    // This query will produce the full path for all .txt files  
    // under the specified folder including subfolders.  
    // It orders the list according to the file name.  
    static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Create the query  
        IEnumerable<System.IO.FileInfo> fileQuery =  
            from file in fileList  
            where file.Extension == ".txt"  
            orderby file.Name  
            select file;  
  
        //Execute the query. This might write out a lot of files!  
        foreach (System.IO.FileInfo fi in fileQuery)  
        {  
            Console.WriteLine(fi.FullName);  
        }  
  
        // Create and execute a new query by using the previous   
        // query as a starting point. fileQuery is not   
        // executed again until the call to Last()  
        var newestFile =  
            (from file in fileQuery  
             orderby file.CreationTime  
             select new { file.FullName, file.CreationTime })  
            .Last();  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}",  
            newestFile.FullName, newestFile.CreationTime);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9251e-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9251e-106">Compiling the Code</span></span>  
  <span data-ttu-id="9251e-107">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="9251e-107">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9251e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9251e-108">See also</span></span>

- [<span data-ttu-id="9251e-109">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="9251e-109">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="9251e-110">LINQ e diretórios de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="9251e-110">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
