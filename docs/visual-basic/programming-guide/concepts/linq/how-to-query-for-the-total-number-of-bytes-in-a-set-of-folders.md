---
title: "Como: consultar o número Total de Bytes em um conjunto de pastas (LINQ) (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 668a8a4d89f7b81c3aef9b4e1a46ad749c4a8341
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Como: consultar o número Total de Bytes em um conjunto de pastas (LINQ) (Visual Basic)
Este exemplo mostra como recuperar o número total de bytes usado por todos os arquivos em uma pasta especificada e todas as suas subpastas.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Linq.Enumerable.Sum%2A>método adiciona os valores de todos os itens selecionados de `select` cláusula.</xref:System.Linq.Enumerable.Sum%2A> Você pode facilmente modificar essa consulta para recuperar o arquivo maior ou menor na árvore de diretório especificado chamando o <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A>método em vez de <xref:System.Linq.Enumerable.Sum%2A>.</xref:System.Linq.Enumerable.Sum%2A> </xref:System.Linq.Enumerable.Max%2A> ou</xref:System.Linq.Enumerable.Min%2A>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Se você tiver apenas contar o número de bytes em uma árvore de diretório especificado, você pode fazer isso com mais eficiência sem criar uma consulta LINQ, que gera a sobrecarga de criação da coleção de lista como uma fonte de dados. A utilidade da abordagem do LINQ aumenta, a consulta se torna mais complexa ou quando você precisa executar várias consultas em relação a mesma fonte de dados.  
  
 A consulta chama um método separado para obter o comprimento de arquivo. Ele faz isso para consumir a possível exceção será gerada se o arquivo foi excluído em outro thread após o <xref:System.IO.FileInfo>objeto foi criado na chamada para `GetFiles`.</xref:System.IO.FileInfo> Embora o <xref:System.IO.FileInfo>objeto já foi criado, a exceção pode ocorrer porque um <xref:System.IO.FileInfo>objeto tentará atualizar seu <xref:System.IO.FileInfo.Length%2A>propriedade com o comprimento máximo atual na primeira vez em que a propriedade é acessada.</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> Ao colocar essa operação em um bloco try-catch fora da consulta, o código segue a regra de evitar operações em consultas que podem causar efeitos colaterais. Em geral, ótimo deve ter cuidado ao consumir exceções para certificar-se de que um aplicativo não seja deixado em um estado desconhecido.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou superior com uma referência a System.Core.dll e uma `Imports` declaração para o namespace System. Linq.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ e diretórios de arquivos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
