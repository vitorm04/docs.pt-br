---
title: "Como: consultar o maior arquivo ou arquivos em uma &#225;rvore de diret&#243;rio (LINQ) (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: consultar o maior arquivo ou arquivos em uma &#225;rvore de diret&#243;rio (LINQ) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra cinco consultas relacionadas ao tamanho do arquivo em bytes:  
  
-   Como recuperar o tamanho em bytes do arquivo maior.  
  
-   Como recuperar o tamanho em bytes do arquivo menor.  
  
-   Como recuperar o <xref:System.IO.FileInfo> arquivo maior ou menor de objetos de uma ou mais pastas em uma pasta raiz especificada.  
  
-   Como recuperar uma seqüência, como os 10 maiores arquivos.  
  
-   Como ordenar os arquivos em grupos com base em seu tamanho de arquivo em bytes, ignorando arquivos que são menores do que um tamanho especificado.  
  
## Exemplo  
 O exemplo a seguir contém cinco consultas separadas que mostram como consultar e arquivos de grupo, dependendo do tamanho do arquivo em bytes. Você pode facilmente modificar esses exemplos para basear a consulta em outra propriedade do <xref:System.IO.FileInfo> objeto.  
  
```c#  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.   
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
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
  
 Para retornar a concluir uma ou mais <xref:System.IO.FileInfo> objetos, a consulta primeiro deve examinar cada um dos dados de origem e, em seguida, classificá\-los pelo valor de sua propriedade de comprimento. Em seguida, ele pode retornar uma única ou a sequência com os maiores tamanhos. Use <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro elemento em uma lista. Use <xref:System.Linq.Enumerable.Take%2A> para retornar o primeiro n número de elementos. Especifica uma ordem de classificação decrescente para colocar os elementos menor no início da lista.  
  
 A consulta chama um método separado para obter o tamanho do arquivo em bytes para consumir a possível exceção ocorrerá no caso em que um arquivo foi excluído em outro thread no período de tempo desde o <xref:System.IO.FileInfo> objeto foi criado na chamada para `GetFiles`. Embora o <xref:System.IO.FileInfo> objeto já foi criado, a exceção pode ocorrer porque um <xref:System.IO.FileInfo> objeto tentará atualizar seu <xref:System.IO.FileInfo.Length%2A> propriedade usando o tamanho máximo atual em bytes a propriedade é acessada pela primeira vez. Ao colocar essa operação em um bloco try\-catch fora da consulta, podemos seguir a regra de evitar operações em consultas que podem causar efeitos colaterais. Em geral, ótimo deve ter cuidado ao consumir exceções, para certificar\-se de que um aplicativo não seja deixado em um estado desconhecido.  
  
## Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou posterior, com uma referência a System.Core.dll e `using` diretivas para os namespaces System. LINQ e System.IO.  
  
## Consulte também  
 [LINQ to Objects \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ e diretórios de arquivo \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)