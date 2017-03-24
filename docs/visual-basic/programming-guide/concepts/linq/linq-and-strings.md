---
title: LINQ e cadeias de caracteres (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a79d1427331070da9c545fdd3175115fe187e879
ms.lasthandoff: 03/13/2017

---
# <a name="linq-and-strings-visual-basic"></a>LINQ e cadeias de caracteres (Visual Basic)
LINQ pode ser usado para consultar e transformar coleções de cadeias de caracteres e cadeias de caracteres. Ele pode ser especialmente útil com dados estruturados em arquivos de texto. Consultas LINQ podem ser combinadas com expressões regulares e funções de cadeia de caracteres tradicional. Por exemplo, você pode usar o <xref:System.String.Split%2A>ou <xref:System.Text.RegularExpressions.Regex.Split%2A>método para criar uma matriz de cadeias de caracteres que você pode consultar ou modificar usando LINQ.</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A> Você pode usar o <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>método de `where` cláusula de uma consulta LINQ.</xref:System.Text.RegularExpressions.Regex.IsMatch%2A> E você pode usar o LINQ para consultar ou modificar o <xref:System.Text.RegularExpressions.MatchCollection>resultados retornados por uma expressão regular.</xref:System.Text.RegularExpressions.MatchCollection>  
  
 Você também pode usar as técnicas descritas nesta seção para transformar dados semi-estruturados texto para XML. Para obter mais informações, consulte [como: gerar XML de arquivos CSV](how-to-generate-xml-from-csv-files.md).  
  
 Os exemplos nesta seção se enquadram em duas categorias:  
  
## <a name="querying-a-block-of-text"></a>Consultando um bloco de texto  
 Você pode consultar, analisar e modificar blocos de texto dividindo-os em uma matriz de cadeias de caracteres menores de que podem ser consultada usando o <xref:System.String.Split%2A>método ou o <xref:System.Text.RegularExpressions.Regex.Split%2A>método.</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A> Você pode dividir o texto de origem em palavras, frases, parágrafos, páginas ou quaisquer outros critérios e, em seguida, executar divisões adicionais se eles forem necessários em sua consulta.  
  
 [Como: contar as ocorrências de uma palavra em uma cadeia de caracteres (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Mostra como usar o LINQ para consultas simples em texto.  
  
 [Como: consultar sentenças que contêm um conjunto especificado de palavras (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Mostra como dividir os arquivos de texto em limites arbitrários e como executar consultas em cada parte.  
  
 [Como: consultar caracteres em uma cadeia de caracteres (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Demonstra uma cadeia de caracteres é um tipo que pode ser consultado.  
  
 [Como: combinar consultas LINQ com expressões regulares (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Mostra como usar expressões regulares em consultas LINQ de padrões complexos correspondentes nos resultados de consulta filtrada.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Consultando dados semi-estruturados em formato de texto  
 Muitos tipos diferentes de arquivos de texto consistem em uma série de linhas, geralmente com formatação semelhante, como arquivos delimitados por tabulação ou vírgula ou linhas de comprimento fixo. Depois de ler um arquivo de texto na memória, você pode usar o LINQ para consultar e/ou modifique as linhas. Consultas LINQ também simplificam a tarefa de combinar dados de várias fontes.  
  
 [Como: localizar a diferença definida entre as duas listas (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Mostra como localizar todas as strings que estão presentes em uma lista, mas não o outro.  
  
 [Como: classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Mostra como classificar linhas de texto com base em qualquer palavra ou campo.  
  
 [Como: reordenar os campos de um arquivo delimitado (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Mostra como reordenar campos em uma linha em um arquivo. csv.  
  
 [Como: combinar e comparar coleções de cadeia de caracteres (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Mostra como combinar listas de cadeia de caracteres de várias maneiras.  
  
 [Como: preencher coleções de objetos de várias fontes (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Mostra como criar coleções de objetos usando vários arquivos de texto, como fontes de dados.  
  
 [Como: unir conteúdo a partir de arquivos diferentes (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 Mostra como combinar cadeias de caracteres em duas listas em uma única cadeia de caracteres usando uma chave correspondente.  
  
 [Como: dividir um arquivo em vários arquivos usando grupos (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Mostra como criar novos arquivos usando um único arquivo como uma fonte de dados.  
  
 [Como: calcular valores de coluna em um arquivo CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Mostra como executar cálculos matemáticos em dados de texto em arquivos. csv.  
  
## <a name="see-also"></a>Consulte também  
 [Consulta integrada à linguagem (LINQ) (Visual Basic)](index.md)   
 [Como gerar um XML de arquivos CSV](how-to-generate-xml-from-csv-files.md)

