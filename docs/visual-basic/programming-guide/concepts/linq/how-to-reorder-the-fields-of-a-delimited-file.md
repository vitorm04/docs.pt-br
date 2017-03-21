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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9abb0510ed3944cd80d6658238ef79d64dc0ca27
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Como: reordenar os campos de um arquivo delimitado (LINQ) (Visual Basic)
Um arquivo de valores separados por vírgulas (CSV) é um arquivo de texto que é geralmente usado para armazenar dados da planilha ou outros dados de tabela que são representados por linhas e colunas. Usando o <xref:System.String.Split%2A>método para separar os campos, é muito fácil consultar e manipular arquivos CSV usando LINQ.</xref:System.String.Split%2A> Na verdade, a mesma técnica pode ser usada para reordenar as partes de qualquer linha estruturada de texto; não é limitado a arquivos CSV.  
  
 O exemplo a seguir, suponha que as três colunas representam os "Sobrenome," alunos "first name" e "ID". Os campos estão em ordem alfabética com base em sobrenomes dos alunos. A consulta gera uma nova sequência na qual a coluna ID é exibido primeira, seguido por uma segunda coluna que combina o nome e sobrenome do aluno. As linhas são reordenadas acordo com o campo ID. Os resultados são salvos em um novo arquivo e os dados originais não são modificados.  
  
### <a name="to-create-the-data-file"></a>Para criar o arquivo de dados  
  
1.  Copie as seguintes linhas em um arquivo de texto sem formatação denominado spreadsheet1.csv. Salve o arquivo na pasta do projeto.  
  
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
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
  
## <a name="see-also"></a>Consulte também  
 [LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [LINQ e diretórios de arquivos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)   
 [Como gerar um XML de arquivos CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
