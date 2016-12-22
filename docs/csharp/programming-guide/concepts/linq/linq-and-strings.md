---
title: "LINQ e cadeias de caracteres (c#) | Microsoft Docs"
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
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# LINQ e cadeias de caracteres (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

LINQ pode ser usado para consultar e transformar coleções de cadeias de caracteres e cadeias de caracteres. Ele pode ser especialmente útil com dados estruturados em arquivos de texto. Consultas LINQ podem ser combinadas com expressões regulares e funções de cadeia de caracteres tradicional. Por exemplo, você pode usar o <xref:System.String.Split%2A> ou <xref:System.Text.RegularExpressions.Regex.Split%2A> método para criar uma matriz de cadeias de caracteres que você pode consultar ou modificar usando LINQ. Você pode usar o <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> método de `where` cláusula de uma consulta LINQ. E você pode usar o LINQ para consultar ou modificar o <xref:System.Text.RegularExpressions.MatchCollection> resultados retornados por uma expressão regular.  
  
 Você também pode usar as técnicas descritas nesta seção para transformar dados semi\-estruturados texto para XML. Para obter mais informações, consulte [How to: Generate XML from CSV Files](../Topic/How%20to:%20Generate%20XML%20from%20CSV%20Files.md).  
  
 Os exemplos nesta seção se enquadram em duas categorias:  
  
## Consultando um bloco de texto  
 Você pode consultar, analisar e modificar blocos de texto dividindo\-os em uma matriz de cadeias de caracteres menores de que podem ser consultada usando o <xref:System.String.Split%2A> método ou o <xref:System.Text.RegularExpressions.Regex.Split%2A> método. Você pode dividir o texto de origem em palavras, frases, parágrafos, páginas ou quaisquer outros critérios e, em seguida, executar divisões adicionais se eles forem necessários em sua consulta.  
  
 [Como: contar as ocorrências de uma palavra em uma cadeia de caracteres \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Mostra como usar o LINQ para consultas simples em texto.  
  
 [Como: consultar sentenças que contêm um conjunto especificado de palavras \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)  
 Mostra como dividir os arquivos de texto em limites arbitrários e como executar consultas em cada parte.  
  
 [Como: consultar caracteres em uma cadeia de caracteres \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-characters-in-a-string-linq.md)  
 Demonstra uma cadeia de caracteres é um tipo que pode ser consultado.  
  
 [Como: combinar consultas LINQ com expressões regulares \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)  
 Mostra como usar expressões regulares em consultas LINQ de padrões complexos correspondentes nos resultados de consulta filtrada.  
  
## Consultando dados semi\-estruturados em formato de texto  
 Muitos tipos diferentes de arquivos de texto consistem em uma série de linhas, geralmente com formatação semelhante, como arquivos delimitados por tabulação ou vírgula ou linhas de comprimento fixo. Depois de ler um arquivo de texto na memória, você pode usar o LINQ para consultar e\/ou modifique as linhas. Consultas LINQ também simplificam a tarefa de combinar dados de várias fontes.  
  
 [Como: localizar a diferença definida entre as duas listas \(LINQ\) \(c\#\)](../Topic/How%20to:%20Find%20the%20Set%20Difference%20Between%20Two%20Lists%20\(LINQ\)%20\(C%23\).md)  
 Mostra como localizar todas as strings que estão presentes em uma lista, mas não o outro.  
  
 [Como: classificar ou filtrar dados de texto por qualquer palavra ou campo \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Mostra como classificar linhas de texto com base em qualquer palavra ou campo.  
  
 [Como: reordenar os campos de um arquivo delimitado \(LINQ\) \(c\#\)](../Topic/How%20to:%20Reorder%20the%20Fields%20of%20a%20Delimited%20File%20\(LINQ\)%20\(C%23\).md)  
 Mostra como reordenar campos em uma linha em um arquivo. csv.  
  
 [Como: combinar e comparar coleções de cadeia de caracteres \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 Mostra como combinar listas de cadeia de caracteres de várias maneiras.  
  
 [Como: preencher coleções de objetos de várias fontes \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Mostra como criar coleções de objetos usando vários arquivos de texto, como fontes de dados.  
  
 [Como: unir conteúdo a partir de arquivos diferentes \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 Mostra como combinar cadeias de caracteres em duas listas em uma única cadeia de caracteres usando uma chave correspondente.  
  
 [Como: dividir um arquivo em vários arquivos usando grupos \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Mostra como criar novos arquivos usando um único arquivo como uma fonte de dados.  
  
 [Como: calcular valores de coluna em um arquivo CSV \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Mostra como executar cálculos matemáticos em dados de texto em arquivos. csv.  
  
## Consulte também  
 [Consulta integrada à linguagem \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/index.md)   
 [How to: Generate XML from CSV Files](../Topic/How%20to:%20Generate%20XML%20from%20CSV%20Files.md)