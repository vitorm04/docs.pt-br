---
title: "LINQ e diretórios de arquivos (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
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
ms.openlocfilehash: 5536ae95b42cdaddda2c4cae97a114681e94b0ab
ms.lasthandoff: 03/13/2017

---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ e diretórios de arquivos (Visual Basic)
Muitas operações de sistema de arquivos são essencialmente consultas e, portanto, são ideais para a abordagem do LINQ.  
  
 Observe que as consultas nesta seção são não-destrutiva. Eles não são usados para alterar o conteúdo dos arquivos originais ou pastas. Isso segue a regra que consultas não devem causar efeitos colaterais. Em geral, qualquer código (incluindo consultas que executam criarem / atualizam / excluir operadores) que modifica os dados de origem deve ser mantido separado do código que consulta apenas os dados.  
  
 Esta seção contém os tópicos a seguir:  
  
 [Como: consultar arquivos com um atributo especificado ou o nome (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Mostra como procurar arquivos examinando uma ou mais propriedades de seu <xref:System.IO.FileInfo>objeto.</xref:System.IO.FileInfo>  
  
 [Como: agrupar arquivos por extensão (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Mostra como retornar os grupos de <xref:System.IO.FileInfo>objeto com base em sua extensão de nome de arquivo.</xref:System.IO.FileInfo>  
  
 [Como: consultar o número Total de Bytes em um conjunto de pastas (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Mostra como retornar o número total de bytes em todos os arquivos em uma árvore de diretório especificado.  
  
 [Como: comparar o conteúdo de duas pastas (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Mostra como retornar todos os arquivos que estão presentes em duas pastas especificadas e também todos os arquivos que estão presentes em uma pasta, mas não o outro.  
  
 [Como: consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Mostra como retornar o arquivo maior ou menor, ou um número especificado de arquivos, em uma árvore de diretório.  
  
 [Como: consultar arquivos duplicados em uma árvore de diretório (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Mostra como agrupar todos os nomes de arquivo que ocorrem em mais de um local em uma árvore de diretório especificado. Também mostra como executar comparações mais complexas com base em um comparador personalizado.  
  
 [Como: consultar o conteúdo de arquivos em uma pasta (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Mostra como iterar através de pastas em uma árvore, abra cada arquivo e consultar o conteúdo do arquivo.  
  
## <a name="comments"></a>Comentários  
 Há alguma complexidade envolvida na criação de uma fonte de dados que representa o conteúdo do sistema de arquivos com precisão e lida com exceções normalmente. Os exemplos nesta seção criam uma coleção de instantâneo de <xref:System.IO.FileInfo>objetos que representa todos os arquivos em uma pasta raiz especificada e todas as suas subpastas.</xref:System.IO.FileInfo> O estado real de cada <xref:System.IO.FileInfo>pode ser alterado no tempo entre quando você começa e terminar a execução de uma consulta.</xref:System.IO.FileInfo> Por exemplo, você pode criar uma lista de <xref:System.IO.FileInfo>objetos para usar como uma fonte de dados.</xref:System.IO.FileInfo> Se você tentar acessar o `Length` propriedade em uma consulta, o <xref:System.IO.FileInfo>objeto tentará acessar o sistema de arquivos para atualizar o valor de `Length`.</xref:System.IO.FileInfo> Se o arquivo não existir, você obterá uma <xref:System.IO.FileNotFoundException>em sua consulta, embora não consultar o sistema de arquivos diretamente.</xref:System.IO.FileNotFoundException> Algumas consultas nesta seção usam um método separado que consome essas exceções específicas em determinados casos. Outra opção é manter a fonte de dados atualizada dinamicamente usando <xref:System.IO.FileSystemWatcher>.</xref:System.IO.FileSystemWatcher>  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
