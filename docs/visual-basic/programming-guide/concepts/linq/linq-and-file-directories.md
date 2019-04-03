---
title: LINQ e diretórios de arquivos (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 56967a82bf63d8421d34af48dcc6384ded85e2ad
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825112"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ e diretórios de arquivos (Visual Basic)
Muitas operações do sistema de arquivos são essencialmente consultas e, portanto, são ideais para a abordagem do LINQ.  
  
 Observe que as consultas nesta seção são não destrutivas. Elas não são usadas para alterar o conteúdo dos arquivos ou pastas originais. Isso segue a regra de que consultas não devem causar efeitos colaterais. Em geral, qualquer código (incluindo consultas que executam operadores criar / atualizar / excluir) que modifique dados de origem deve ser mantido separado do código que apenas consulta os dados.  
  
 Esta seção contém os tópicos a seguir:  
  
 [Como: Consultar arquivos com um atributo especificado ou o nome (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Mostra como pesquisar arquivos, examinando uma ou mais propriedades de seu objeto <xref:System.IO.FileInfo>.  
  
 [Como: Agrupar arquivos por extensão (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Mostra como retornar grupos de objetos <xref:System.IO.FileInfo> com base em sua extensão de nome de arquivo.  
  
 [Como: Consultar o número Total de Bytes em um conjunto de pastas (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Mostra como retornar o número total de bytes em todos os arquivos de uma árvore de diretórios especificada.  
  
 [Como: Comparar o conteúdo de duas pastas (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Mostra como retornar todos os arquivos que estão presentes em duas pastas especificadas e também todos os arquivos que estão presentes em uma pasta, mas não na outra.  
  
 [Como: Consulta para o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Mostra como retornar o maior ou o menor arquivo ou um número especificado de arquivos, em uma árvore de diretório.  
  
 [Como: Consultar arquivos duplicados em uma árvore de diretório (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Mostra como agrupar todos os nomes de arquivo que ocorrem em mais de um local em uma árvore de diretórios especificada. Também mostra como realizar comparações mais complexas com base em um comparador personalizado.  
  
 [Como: Consultar o conteúdo de arquivos em uma pasta (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Mostra como iterar pelas pastas em uma árvore, abrir cada arquivo e consultar o conteúdo do arquivo.  
  
## <a name="comments"></a>Comentários  
 Há certa complexidade envolvida na criação de uma fonte de dados que representa o conteúdo do sistema de arquivos com precisão e trata exceções de maneira elegante. Os exemplos nesta seção criam uma coleção de instantâneos de objetos <xref:System.IO.FileInfo> que representa todos os arquivos em uma pasta raiz especificada e todas as suas subpastas. O estado real de cada <xref:System.IO.FileInfo> pode ser alterado no tempo entre o momento em que você começa e termina a execução de uma consulta. Por exemplo, você pode criar uma lista de objetos <xref:System.IO.FileInfo> para usar como uma fonte de dados. Se você tentar acessar a propriedade `Length` em uma consulta, o objeto <xref:System.IO.FileInfo> tentará acessar o sistema de arquivos para atualizar o valor de `Length`. Se o arquivo não existir, você obterá uma <xref:System.IO.FileNotFoundException> em sua consulta, embora não esteja consultando diretamente o sistema de arquivos. Algumas consultas nesta seção usam um método separado que consome essas exceções específicas em determinados casos. Outra opção é manter a fonte de dados atualizada dinamicamente usando o <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Consulte também

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
