---
title: "Como: preencher cole&#231;&#245;es de objetos de v&#225;rias fontes (LINQ) (c#) | Microsoft Docs"
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
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: preencher cole&#231;&#245;es de objetos de v&#225;rias fontes (LINQ) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como mesclar dados de diferentes origens em uma sequência de novos tipos.  
  
> [!NOTE]
>  Não tente unir dados na memória ou dados no sistema de arquivos com dados que ainda está em um banco de dados. Essas associações entre domínios podem gerar resultados indefinidos devido às diferentes formas em que as operações de associação podem ser definidas para consultas de banco de dados e outros tipos de fontes. Além disso, há um risco de que essa operação pode causar uma exceção de falta de memória, se a quantidade de dados no banco de dados é grande o suficiente. Para associar dados de um banco de dados para dados na memória, primeiro chame `ToList` ou `ToArray` no banco de dados de consulta e, em seguida, execute a junção na coleção retornada.  
  
### Para criar o arquivo de dados  
  
-   Copie os arquivos names.csv e scores.csv para a pasta do projeto, conforme descrito em [Como: unir conteúdo a partir de arquivos diferentes \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).  
  
## Exemplo  
 O exemplo a seguir mostra como usar um tipo nomeado `Student` para armazenar dados mesclados de duas coleções na memória de cadeias de caracteres que simulam dados da planilha no formato. csv. O primeiro conjunto de cadeias de caracteres representando os nomes dos alunos e IDs e a segunda coleção representa a ID do aluno \(na primeira coluna\) e quatro pontuações de exame. A ID é usada como a chave estrangeira.  
  
```c#  
class Student  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int ID { get; set; }  
    public List<int> ExamScores { get; set; }  
}  
  
class PopulateCollection  
{  
    static void Main()  
    {  
        // These data files are defined in How to: Join Content from   
        // Dissimilar Files (LINQ).  
  
        // Each line of names.csv consists of a last name, a first name, and an  
        // ID number, separated by commas. For example, Omelchenko,Svetlana,111  
        string[] names = System.IO.File.ReadAllLines(@"../../../names.csv");  
  
        // Each line of scores.csv consists of an ID number and four test   
        // scores, separated by commas. For example, 111, 97, 92, 81, 60  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Merge the data sources using a named type.  
        // var could be used instead of an explicit type. Note the dynamic  
        // creation of a list of ints for the ExamScores member. We skip   
        // the first item in the split string because it is the student ID,   
        // not an exam score.  
        IEnumerable<Student> queryNamesScores =  
            from nameLine in names  
            let splitName = nameLine.Split(',')  
            from scoreLine in scores  
            let splitScoreLine = scoreLine.Split(',')  
            where splitName[2] == splitScoreLine[0]  
            select new Student()  
            {  
                FirstName = splitName[0],  
                LastName = splitName[1],  
                ID = Convert.ToInt32(splitName[2]),  
                ExamScores = (from scoreAsText in splitScoreLine.Skip(1)  
                              select Convert.ToInt32(scoreAsText)).  
                              ToList()  
            };  
  
        // Optional. Store the newly created student objects in memory  
        // for faster access in future queries. This could be useful with  
        // very large data files.  
        List<Student> students = queryNamesScores.ToList();  
  
        // Display each student's name and exam score average.  
        foreach (var student in students)  
        {  
            Console.WriteLine("The average score of {0} {1} is {2}.",  
                student.FirstName, student.LastName,  
                student.ExamScores.Average());  
        }  
  
        //Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
}  
/* Output:   
    The average score of Omelchenko Svetlana is 82.5.  
    The average score of O'Donnell Claire is 72.25.  
    The average score of Mortensen Sven is 84.5.  
    The average score of Garcia Cesar is 88.25.  
    The average score of Garcia Debra is 67.  
    The average score of Fakhouri Fadi is 92.25.  
    The average score of Feng Hanying is 88.  
    The average score of Garcia Hugo is 85.75.  
    The average score of Tucker Lance is 81.75.  
    The average score of Adams Terry is 85.25.  
    The average score of Zabokritski Eugene is 83.  
    The average score of Tucker Michael is 92.  
 */  
```  
  
 No [Selecione](../../../../csharp/language-reference/keywords/select-clause.md) cláusula, um inicializador de objeto é usada para criar uma instância de cada novo `Student` objeto usando os dados de duas origens.  
  
 Se você não tiver que armazenar os resultados de uma consulta, tipos anônimos podem ser mais convenientes que tipos nomeados. Tipos nomeados são necessários se você passar os resultados da consulta fora do método em que a consulta é executada. O exemplo a seguir executa a mesma tarefa do exemplo anterior, mas usa tipos anônimos em vez de tipos nomeados:  
  
```c#  
// Merge the data sources by using an anonymous type.  
// Note the dynamic creation of a list of ints for the  
// ExamScores member. We skip 1 because the first string  
// in the array is the student ID, not an exam score.  
var queryNamesScores2 =  
    from nameLine in names  
    let splitName = nameLine.Split(',')  
    from scoreLine in scores  
    let splitScoreLine = scoreLine.Split(',')  
    where splitName[2] == splitScoreLine[0]  
    select new  
    {  
        First = splitName[0],  
        Last = splitName[1],  
        ExamScores = (from scoreAsText in splitScoreLine.Skip(1)  
                      select Convert.ToInt32(scoreAsText))  
                      .ToList()  
    };  
  
// Display each student's name and exam score average.  
foreach (var student in queryNamesScores2)  
{  
    Console.WriteLine("The average score of {0} {1} is {2}.",  
        student.First, student.Last, student.ExamScores.Average());  
}  
```  
  
## Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou posterior, com uma referência a System.Core.dll e `using` diretivas para os namespaces System. LINQ e System.IO.  
  
## Consulte também  
 [LINQ e cadeias de caracteres \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)   
 [Inicializadores de objeto e coleção](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [Tipos anônimos](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)