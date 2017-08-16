---
title: "Como: consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 055cbdd5a5903417ab382d390e1215f0319c0b5a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Como: consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)
Este exemplo mostra cinco consultas relacionadas ao tamanho do arquivo em bytes:  
  
-   Como recuperar o tamanho em bytes do arquivo maior.  
  
-   Como recuperar o tamanho em bytes do arquivo menor.  
  
-   Como recuperar o <xref:System.IO.FileInfo>arquivo maior ou menor de objetos de uma ou mais pastas em uma pasta raiz especificada.</xref:System.IO.FileInfo>  
  
-   Como recuperar uma sequência, como os 10 maiores arquivos.  
  
-   Como ordenar os arquivos em grupos com base em seu tamanho de arquivo em bytes, ignorando arquivos que são menores do que um tamanho especificado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém cinco consultas separadas que mostram como consultar e arquivos de grupo, dependendo do tamanho do arquivo em bytes. Você pode facilmente modificar esses exemplos para basear a consulta em outra propriedade do <xref:System.IO.FileInfo>objeto.</xref:System.IO.FileInfo>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Para retornar a concluir uma ou mais <xref:System.IO.FileInfo>objetos, a consulta primeiro deve examinar cada um dos dados de origem e, em seguida, classificá-los pelo valor de sua propriedade Length.</xref:System.IO.FileInfo> Em seguida, ele pode retornar uma única ou a sequência com os maiores tamanhos. Use <xref:System.Linq.Enumerable.First%2A>para retornar o primeiro elemento em uma lista.</xref:System.Linq.Enumerable.First%2A> Use <xref:System.Linq.Enumerable.Take%2A>para retornar o primeiro número de n elementos.</xref:System.Linq.Enumerable.Take%2A> Especifica uma ordem de classificação decrescente para colocar os elementos menor no início da lista.  
  
 A consulta chama um método separado para obter o tamanho do arquivo em bytes para consumir a possível exceção ocorrerá no caso em que um arquivo foi excluído em outro thread no período de tempo desde o <xref:System.IO.FileInfo>objeto foi criado na chamada para `GetFiles`.</xref:System.IO.FileInfo> Embora o <xref:System.IO.FileInfo>objeto já foi criado, a exceção pode ocorrer porque um <xref:System.IO.FileInfo>objeto tentará atualizar seu <xref:System.IO.FileInfo.Length%2A>propriedade usando o tamanho máximo atual em bytes na primeira vez em que a propriedade é acessada.</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> Ao colocar essa operação em um bloco try-catch fora da consulta, podemos seguir a regra de evitar operações em consultas que podem causar efeitos colaterais. Em geral, ótimo deve ter cuidado ao consumir exceções, para certificar-se de que um aplicativo não seja deixado em um estado desconhecido.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou superior com uma referência a System.Core.dll e uma `Imports` declaração para o namespace System. Linq.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ e diretórios de arquivos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
