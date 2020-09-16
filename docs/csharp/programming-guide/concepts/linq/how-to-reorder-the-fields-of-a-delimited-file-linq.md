---
title: Como reordenar os campos de um arquivo delimitado (LINQ) (C#)
description: Saiba como reorganizar os campos em um arquivo. csv no LINQ em C#. O exemplo altera as ordens de colunas, mescla em colunas e classifica as linhas por um valor de coluna.
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: a3bbc2690ded24629b313b24ee7a604bcacce850
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547291"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="1603c-104">Como reordenar os campos de um arquivo delimitado (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1603c-104">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>
<span data-ttu-id="1603c-105">Um CSV (arquivo de valores separados por vírgula) é um arquivo de texto que é frequentemente usado para armazenar dados de planilha ou outros dados de tabela que são representados por linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="1603c-105">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="1603c-106">Ao usar o método <xref:System.String.Split%2A> para separar os campos, é muito fácil consultar e manipular arquivos CSV usando LINQ.</span><span class="sxs-lookup"><span data-stu-id="1603c-106">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="1603c-107">Na verdade, a mesma técnica pode ser usada para reordenar as partes de qualquer linha estruturada de texto. Ela não é limitada a arquivos CSV.</span><span class="sxs-lookup"><span data-stu-id="1603c-107">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="1603c-108">No exemplo a seguir, suponha que as três colunas representam o "sobrenome", o "nome" e a "ID" dos alunos.</span><span class="sxs-lookup"><span data-stu-id="1603c-108">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="1603c-109">Os campos estão em ordem alfabética com base nos sobrenomes dos alunos.</span><span class="sxs-lookup"><span data-stu-id="1603c-109">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="1603c-110">A consulta gera uma nova sequência, na qual a coluna ID é exibida em primeiro, seguida por uma segunda coluna que combina o nome e o sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="1603c-110">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="1603c-111">As linhas são reordenadas acordo com o campo ID.</span><span class="sxs-lookup"><span data-stu-id="1603c-111">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="1603c-112">Os resultados são salvos em um novo arquivo e os dados originais não são modificados.</span><span class="sxs-lookup"><span data-stu-id="1603c-112">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="1603c-113">Para criar o arquivo de dados</span><span class="sxs-lookup"><span data-stu-id="1603c-113">To create the data file</span></span>  
  
1. <span data-ttu-id="1603c-114">Copie as seguintes linhas em um arquivo de texto sem formatação denominado spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="1603c-114">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="1603c-115">Salve o arquivo na pasta do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1603c-115">Save the file in your project folder.</span></span>  
  
    ```csv  
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
  
## <a name="example"></a><span data-ttu-id="1603c-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1603c-116">Example</span></span>  
  
```csharp  
class CSVFiles  
{  
    static void Main(string[] args)  
    {  
        // Create the IEnumerable data source  
        string[] lines = System.IO.File.ReadAllLines(@"../../../spreadsheet1.csv");  
  
        // Create the query. Put field 2 first, then  
        // reverse and combine fields 0 and 1 from the old field  
        IEnumerable<string> query =  
            from line in lines  
            let x = line.Split(',')  
            orderby x[2]  
            select x[2] + ", " + (x[1] + " " + x[0]);  
  
        // Execute the query and write out the new file. Note that WriteAllLines  
        // takes a string[], so ToArray is called on the query.  
        System.IO.File.WriteAllLines(@"../../../spreadsheet2.csv", query.ToArray());  
  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output to spreadsheet2.csv:  
111, Svetlana Omelchenko  
112, Claire O'Donnell  
113, Sven Mortensen  
114, Cesar Garcia  
115, Debra Garcia  
116, Fadi Fakhouri  
117, Hanying Feng  
118, Hugo Garcia  
119, Lance Tucker  
120, Terry Adams  
121, Eugene Zabokritski  
122, Michael Tucker  
 */  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1603c-117">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1603c-117">Compiling the Code</span></span>  
<span data-ttu-id="1603c-118">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="1603c-118">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1603c-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="1603c-119">See also</span></span>

- [<span data-ttu-id="1603c-120">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="1603c-120">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="1603c-121">LINQ e diretórios de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="1603c-121">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="1603c-122">Como gerar XML de arquivos CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="1603c-122">How to generate XML from CSV files (C#)</span></span>](../../../../standard/linq/generate-xml-csv-files.md)
