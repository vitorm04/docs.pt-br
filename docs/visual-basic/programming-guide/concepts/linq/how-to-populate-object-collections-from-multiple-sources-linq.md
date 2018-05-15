---
title: 'Como: preencher coleções de objetos de várias fontes (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: e890900cd2f53e62a55adef56bfdb27b9787d598
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="f2808-102">Como: preencher coleções de objetos de várias fontes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2808-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="f2808-103">Este exemplo mostra como mesclar dados de diferentes fontes em uma sequência de novos tipos.</span><span class="sxs-lookup"><span data-stu-id="f2808-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2808-104">Não tente unir dados na memória ou dados no sistema de arquivos com os dados que ainda estão em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f2808-104">Do not try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="f2808-105">Essas junções entre domínios podem gerar resultados indefinidos, devido às diferentes formas em que as operações de junção podem ser definidas para consultas de banco de dados e outros tipos de fontes.</span><span class="sxs-lookup"><span data-stu-id="f2808-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="f2808-106">Além disso, há um risco de que essa operação possa causar uma exceção de falta de memória, se a quantidade de dados no banco de dados for grande o suficiente.</span><span class="sxs-lookup"><span data-stu-id="f2808-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="f2808-107">Para unir dados de um banco de dados com os dados na memória, primeiro chame `ToList` ou `ToArray` na consulta de banco de dados e, em seguida, realize a junção na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="f2808-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="f2808-108">Para criar o arquivo de dados</span><span class="sxs-lookup"><span data-stu-id="f2808-108">To create the data file</span></span>  
  
-   <span data-ttu-id="f2808-109">Copie os arquivos names.csv e scores.csv em sua pasta de projeto, conforme descrito em [como: unir conteúdo de arquivos diferentes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="f2808-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2808-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f2808-110">Example</span></span>  
 <span data-ttu-id="f2808-111">O exemplo a seguir mostra como usar um tipo nomeado `Student` para armazenar dados mesclados, de duas coleções na memória de cadeias de caracteres, que simulam dados de planilha no formato .csv.</span><span class="sxs-lookup"><span data-stu-id="f2808-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="f2808-112">A primeira coleção de cadeias de caracteres representa os nomes e as IDs dos alunos e a segunda coleção, representa a ID do aluno (na primeira coluna) e quatro pontuações de exames.</span><span class="sxs-lookup"><span data-stu-id="f2808-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="f2808-113">A ID é usada como a chave estrangeira.</span><span class="sxs-lookup"><span data-stu-id="f2808-113">The ID is used as the foreign key.</span></span>  
  
```vb  
Class Student  
    Public FirstName As String  
    Public LastName As String  
    Public ID As Integer  
    Public ExamScores As List(Of Integer)  
End Class  
  
Class PopulateCollection  
  
    Shared Sub Main()  
  
        ' Merge content from spreadsheets into a list of Student objects.  
  
        ' These data files are defined in How to: Join Content from   
        ' Dissimilar Files (LINQ).  
  
        ' Each line of names.csv consists of a last name, a first name, and an  
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111  
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")  
  
        ' Each line of scores.csv consists of an ID number and four test   
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' The following query merges the content of two dissimilar spreadsheets   
        ' based on common ID values.  
        ' Multiple From clauses are used instead of a Join clause  
        ' in order to store the results of scoreLine.Split.  
        ' Note the dynamic creation of a list of integers for the  
        ' ExamScores member. We skip the first item in the split string   
        ' because it is the student ID, not an exam score.  
        Dim queryNamesScores = From nameLine In names  
                          Let splitName = nameLine.Split(New Char() {","})  
                          From scoreLine In scores  
                          Let splitScoreLine = scoreLine.Split(New Char() {","})  
                          Where splitName(2) = splitScoreLine(0)  
                          Select New Student() With {  
                               .FirstName = splitName(0), .LastName = splitName(1), .ID = splitName(2),  
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1  
                                             Select Convert.ToInt32(scoreAsText)).ToList()}  
  
        ' Optional. Store the query results for faster access in future  
        ' queries. This could be useful with very large data files.  
        Dim students As List(Of Student) = queryNamesScores.ToList()  
  
        ' Display each student's name and exam score average.  
        For Each s In students  
            Console.WriteLine("The average score of " & s.FirstName & " " &  
                              s.LastName & " is " & s.ExamScores.Average())  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
  
' Output:   
' The average score of Omelchenko Svetlana is 82.5  
' The average score of O'Donnell Claire is 72.25  
' The average score of Mortensen Sven is 84.5  
' The average score of Garcia Cesar is 88.25  
' The average score of Garcia Debra is 67  
' The average score of Fakhouri Fadi is 92.25  
' The average score of Feng Hanying is 88  
' The average score of Garcia Hugo is 85.75  
' The average score of Tucker Lance is 81.75  
' The average score of Adams Terry is 85.25  
' The average score of Zabokritski Eugene is 83  
' The average score of Tucker Michael is 92  
```  
  
 <span data-ttu-id="f2808-114">No [cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md) cláusula, um inicializador de objeto é usada para criar uma instância de cada novo `Student` objeto por meio de duas fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="f2808-114">In the [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>  
  
 <span data-ttu-id="f2808-115">Se você não tiver que armazenar os resultados de uma consulta, os tipos anônimos poderão ser mais convenientes que os tipos nomeados.</span><span class="sxs-lookup"><span data-stu-id="f2808-115">If you do not have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="f2808-116">Os tipos nomeados são necessários se você passa os resultados da consulta para fora do método em que a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="f2808-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="f2808-117">O exemplo a seguir realiza a mesma tarefa do exemplo anterior, mas usa tipos anônimos em vez de tipos nomeados:</span><span class="sxs-lookup"><span data-stu-id="f2808-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>  
  
```vb  
' Merge the data by using an anonymous type.   
' Note the dynamic creation of a list of integers for the  
' ExamScores member. We skip 1 because the first string  
' in the array is the student ID, not an exam score.  
Dim queryNamesScores2 =  
    From nameLine In names  
    Let splitName = nameLine.Split(New Char() {","})  
    From scoreLine In scores  
    Let splitScoreLine = scoreLine.Split(New Char() {","})  
    Where splitName(2) = splitScoreLine(0)  
    Select New With  
           {.Last = splitName(0),  
            .First = splitName(1),  
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1  
                           Select Convert.ToInt32(scoreAsText)).ToList()}  
  
' Display each student's name and exam score average.  
For Each s In queryNamesScores2  
    Console.WriteLine("The average score of " & s.First & " " &  
                      s.Last & " is " & s.ExamScores.Average())  
Next  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2808-118">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f2808-118">Compiling the Code</span></span>  
 <span data-ttu-id="f2808-119">Crie um projeto que tenha como alvo o .NET Framework versão 3.5 ou posterior com uma referência a System.Core.dll e uma instrução `Imports` para o namespace System.Linq.</span><span class="sxs-lookup"><span data-stu-id="f2808-119">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2808-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2808-120">See Also</span></span>  
 [<span data-ttu-id="f2808-121">LINQ e cadeias de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2808-121">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
