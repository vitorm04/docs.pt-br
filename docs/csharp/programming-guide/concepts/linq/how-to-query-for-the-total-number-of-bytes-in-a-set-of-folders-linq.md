---
title: "Como: consultar o n&#250;mero Total de Bytes em um conjunto de pastas (LINQ) (c#) | Microsoft Docs"
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
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: consultar o n&#250;mero Total de Bytes em um conjunto de pastas (LINQ) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como recuperar o número total de bytes usado por todos os arquivos em uma pasta especificada e todas as suas subpastas.  
  
## Exemplo  
 O <xref:System.Linq.Enumerable.Sum%2A> método adiciona os valores de todos os itens selecionados de `select` cláusula. Você pode facilmente modificar essa consulta para recuperar o arquivo maior ou menor na árvore de diretório especificado chamando o <xref:System.Linq.Enumerable.Min%2A> ou <xref:System.Linq.Enumerable.Max%2A> método em vez de <xref:System.Linq.Enumerable.Sum%2A>.  
  
```c#  
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
  
 Se você tiver apenas contar o número de bytes em uma árvore de diretório especificado, você pode fazer isso com mais eficiência sem criar uma consulta LINQ, que gera a sobrecarga de criação da coleção de lista como uma fonte de dados. A utilidade da abordagem do LINQ aumenta, a consulta se torna mais complexa ou quando você precisa executar várias consultas em relação a mesma fonte de dados.  
  
 A consulta chama um método separado para obter o comprimento de arquivo. Ele faz isso para consumir a possível exceção será gerada se o arquivo foi excluído em outro thread após o <xref:System.IO.FileInfo> objeto foi criado na chamada para `GetFiles`. Embora o <xref:System.IO.FileInfo> objeto já foi criado, a exceção pode ocorrer porque um <xref:System.IO.FileInfo> objeto tentará atualizar seu <xref:System.IO.FileInfo.Length%2A> propriedade com o comprimento máximo atual na primeira vez em que a propriedade é acessada. Ao colocar essa operação em um bloco try\-catch fora da consulta, o código segue a regra de evitar operações em consultas que podem causar efeitos colaterais. Em geral, ótimo deve ter cuidado ao consumir exceções para certificar\-se de que um aplicativo não seja deixado em um estado desconhecido.  
  
## Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou posterior, com uma referência a System.Core.dll e `using` diretivas para os namespaces System. LINQ e System.IO.  
  
## Consulte também  
 [LINQ to Objects \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ e diretórios de arquivo \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)