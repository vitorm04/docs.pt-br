---
title: 'Como: reordenar os campos de um arquivo delimitado (LINQ) (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8540dff06e146a1846063e11e3382e9457f9e412
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="c0571-102">Como: reordenar os campos de um arquivo delimitado (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0571-102">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="c0571-103">Um arquivo de valores separados por vírgulas (CSV) é um arquivo de texto que é geralmente usado para armazenar dados da planilha ou outros dados de tabela que são representados por linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="c0571-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="c0571-104">Usando o <xref:System.String.Split%2A>método para separar os campos, é muito fácil consultar e manipular arquivos CSV usando LINQ.</xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="c0571-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="c0571-105">Na verdade, a mesma técnica pode ser usada para reordenar as partes de qualquer linha estruturada de texto; não é limitado a arquivos CSV.</span><span class="sxs-lookup"><span data-stu-id="c0571-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="c0571-106">O exemplo a seguir, suponha que as três colunas representam os "Sobrenome," alunos "first name" e "ID".</span><span class="sxs-lookup"><span data-stu-id="c0571-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="c0571-107">Os campos estão em ordem alfabética com base em sobrenomes dos alunos.</span><span class="sxs-lookup"><span data-stu-id="c0571-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="c0571-108">A consulta gera uma nova sequência na qual a coluna ID é exibido primeira, seguido por uma segunda coluna que combina o nome e sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="c0571-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="c0571-109">As linhas são reordenadas acordo com o campo ID.</span><span class="sxs-lookup"><span data-stu-id="c0571-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="c0571-110">Os resultados são salvos em um novo arquivo e os dados originais não são modificados.</span><span class="sxs-lookup"><span data-stu-id="c0571-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="c0571-111">Para criar o arquivo de dados</span><span class="sxs-lookup"><span data-stu-id="c0571-111">To create the data file</span></span>  
  
1.  <span data-ttu-id="c0571-112">Copie as seguintes linhas em um arquivo de texto sem formatação denominado spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="c0571-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="c0571-113">Salve o arquivo na pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0571-113">Save the file in your project folder.</span></span>  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a><span data-ttu-id="c0571-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0571-114">Example</span></span>  
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c0571-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c0571-115">Compiling the Code</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0571-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0571-116">See Also</span></span>  
 <span data-ttu-id="c0571-117">[LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="c0571-117">[LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="c0571-118"> [LINQ e diretórios de arquivos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md) </span><span class="sxs-lookup"><span data-stu-id="c0571-118"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md) </span></span>  
<span data-ttu-id="c0571-119"> [Como gerar um XML de arquivos CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)</span><span class="sxs-lookup"><span data-stu-id="c0571-119"> [How to: Generate XML from CSV Files](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)</span></span>
