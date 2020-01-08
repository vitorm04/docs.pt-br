---
title: Como consultar o número total de bytes em um conjunto de pastas (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: c6bfe6bb6d76e7ce8ea8887eef85cd64f2a025df
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344824"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="98404-102">Como consultar o número total de bytes em um conjunto de pastas (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="98404-102">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>
<span data-ttu-id="98404-103">Este exemplo mostra como recuperar o número total de bytes usado por todos os arquivos em uma pasta especificada e todas as suas subpastas.</span><span class="sxs-lookup"><span data-stu-id="98404-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98404-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98404-104">Example</span></span>  
 <span data-ttu-id="98404-105">O método <xref:System.Linq.Enumerable.Sum%2A> adiciona os valores de todos os itens selecionados na cláusula `select`.</span><span class="sxs-lookup"><span data-stu-id="98404-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="98404-106">Você pode modificar essa consulta para recuperar o maior ou o menor arquivo na árvore de diretório especificada chamando o método <xref:System.Linq.Enumerable.Min%2A> ou <xref:System.Linq.Enumerable.Max%2A> em vez de <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="98404-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```csharp  
class QuerySize  
{  
    public static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\VC#";  
  
        // Take a snapshot of the file system.  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<string> fileList = System.IO.Directory.GetFiles(startFolder, "*.*", System.IO.SearchOption.AllDirectories);  
  
        var fileQuery = from file in fileList  
                        select GetFileLength(file);  
  
        // Cache the results to avoid multiple trips to the file system.  
        long[] fileLengths = fileQuery.ToArray();  
  
        // Return the size of the largest file  
        long largestFile = fileLengths.Max();  
  
        // Return the total number of bytes in all the files under the specified folder.  
        long totalBytes = fileLengths.Sum();  
  
        Console.WriteLine("There are {0} bytes in {1} files under {2}",  
            totalBytes, fileList.Count(), startFolder);  
        Console.WriteLine("The largest files is {0} bytes.", largestFile);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the System.IO.FileInfo.Length property.  
    static long GetFileLength(string filename)  
    {  
        long retval;  
        try  
        {  
            System.IO.FileInfo fi = new System.IO.FileInfo(filename);  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
}  
```  
  
 <span data-ttu-id="98404-107">Se precisar apenas contar o número de bytes em uma árvore de diretório especificada, você pode fazer isso com mais eficiência sem criar uma consulta LINQ, que gera a sobrecarga de criação da coleção de lista como uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="98404-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="98404-108">A utilidade da abordagem da LINQ aumenta conforme a consulta se torna mais complexa ou quando você precisa executar várias consultas na mesma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="98404-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="98404-109">A consulta chama um método separado para obter o tamanho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="98404-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="98404-110">Ela faz isso para consumir a possível exceção que será gerada se o arquivo tiver sido excluído em outro thread após o objeto <xref:System.IO.FileInfo> ter sido criado na chamada para `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="98404-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="98404-111">Embora o objeto <xref:System.IO.FileInfo> já tenha sido criado, a exceção poderá ocorrer porque um objeto <xref:System.IO.FileInfo> tentará atualizar sua propriedade <xref:System.IO.FileInfo.Length%2A> com o tamanho mais atual na primeira vez que a propriedade foi acessada.</span><span class="sxs-lookup"><span data-stu-id="98404-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="98404-112">Ao colocar essa operação em um bloco try-catch fora da consulta, o código segue a regra de evitar operações em consultas que podem causar efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="98404-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="98404-113">Em geral, deve-se ter muito cuidado ao consumir exceções para garantir que um aplicativo não seja deixado em um estado desconhecido.</span><span class="sxs-lookup"><span data-stu-id="98404-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98404-114">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="98404-114">Compiling the Code</span></span>  
<span data-ttu-id="98404-115">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="98404-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98404-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="98404-116">See also</span></span>

- [<span data-ttu-id="98404-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="98404-117">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="98404-118">LINQ e diretórios de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="98404-118">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
