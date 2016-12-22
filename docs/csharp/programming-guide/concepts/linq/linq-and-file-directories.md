---
title: "LINQ e diret&#243;rios de arquivo (c#) | Microsoft Docs"
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
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# LINQ e diret&#243;rios de arquivo (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Muitas operações de sistema de arquivos são essencialmente consultas e, portanto, são ideais para a abordagem do LINQ.  
  
 Observe que as consultas nesta seção são não\-destrutiva. Eles não são usados para alterar o conteúdo dos arquivos originais ou pastas. Isso segue a regra que consultas não devem causar efeitos colaterais. Em geral, qualquer código \(incluindo consultas que executam criarem \/ atualizam \/ excluir operadores\) que modifica os dados de origem deve ser mantido separado do código que consulta apenas os dados.  
  
 Esta seção contém os tópicos a seguir:  
  
 [Como: consultar arquivos com um atributo ou nome especificado \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Mostra como procurar arquivos examinando uma ou mais propriedades de seu <xref:System.IO.FileInfo> objeto.  
  
 [Como: agrupar arquivos por extensão \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Mostra como retornar os grupos de <xref:System.IO.FileInfo> objeto com base em sua extensão de nome de arquivo.  
  
 [Como: consultar o número Total de Bytes em um conjunto de pastas \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 Mostra como retornar o número total de bytes em todos os arquivos em uma árvore de diretório especificado.  
  
 [Como: comparar o conteúdo de duas pastas \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Mostra como retornar todos os arquivos que estão presentes em duas pastas especificadas e também todos os arquivos que estão presentes em uma pasta, mas não o outro.  
  
 [Como: consultar o maior arquivo ou arquivos em uma árvore de diretório \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 Mostra como retornar o arquivo maior ou menor, ou um número especificado de arquivos, em uma árvore de diretório.  
  
 [Como: consultar arquivos duplicados em uma árvore de diretório \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Mostra como agrupar todos os nomes de arquivo que ocorrem em mais de um local em uma árvore de diretório especificado. Também mostra como executar comparações mais complexas com base em um comparador personalizado.  
  
 [Como: consultar o conteúdo de arquivos em uma pasta \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 Mostra como iterar através de pastas em uma árvore, abra cada arquivo e consultar o conteúdo do arquivo.  
  
## Comentários  
 Há alguma complexidade envolvida na criação de uma fonte de dados que representa o conteúdo do sistema de arquivos com precisão e lida com exceções normalmente. Os exemplos nesta seção criam uma coleção de instantâneo de <xref:System.IO.FileInfo> objetos que representa todos os arquivos em uma pasta raiz especificada e todas as suas subpastas. O estado real de cada <xref:System.IO.FileInfo> pode ser alterado no tempo entre quando você começa e terminar a execução de uma consulta. Por exemplo, você pode criar uma lista de <xref:System.IO.FileInfo> objetos para usar como uma fonte de dados. Se você tentar acessar o `Length` propriedade em uma consulta, o <xref:System.IO.FileInfo> objeto tentará acessar o sistema de arquivos para atualizar o valor de `Length`. Se o arquivo não existir, você obterá uma <xref:System.IO.FileNotFoundException> em sua consulta, embora não consultar o sistema de arquivos diretamente. Algumas consultas nesta seção usam um método separado que consome essas exceções específicas em determinados casos. Outra opção é manter a fonte de dados atualizada dinamicamente usando o <xref:System.IO.FileSystemWatcher>.  
  
## Consulte também  
 [LINQ to Objects \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)