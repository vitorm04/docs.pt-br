---
title: Modificando árvores XML (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: c946052beb612c087d26e312875b7f7950ceadf5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353182"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Modifying XML Trees (LINQ to XML) (Visual Basic)
O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é um repositório na memória para uma árvore XML. Depois que você carrega ou analisa uma árvore XML de uma fonte, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permite modificar essa árvore no lugar e, em seguida, serializar a árvore, talvez salvando-a em um arquivo ou enviando-a a um servidor remoto.  
  
 Quando você modifica uma árvore no lugar, você usa determinados métodos, como o <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 No entanto, há outra abordagem, que é usar a construção funcional para gerar uma nova árvore com uma outra forma. Dependendo dos tipos de alterações que você precisa fazer em sua árvore XML e do tamanho da árvore, essa abordagem pode ser mais robusta e mais fácil de desenvolver. O primeiro tópico desta seção compara essas duas abordagens.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|Compara a modificação de uma árvore XML na memória com a construção funcional.|  
|[Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Fornece informações sobre como adicionar elementos, atributos ou nós a uma árvore XML.|  
|[Modificação de elementos, atributos e nós em uma árvore XML](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Fornece informações sobre como modificar elementos, atributos ou nós existentes.|  
|[Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Fornece informações sobre como remover elementos, atributos ou nós da árvore XML.|  
|[Maintaining Name/Value Pairs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Descreve como manter informações do aplicativo que são melhor mantidas como pares nome/valor, como informações de configuração ou configurações globais.|  
|[How to: Change the Namespace for an Entire XML Tree (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Mostra como mover uma árvore XML de um namespace para outro.|  
  
## <a name="see-also"></a>Consulte também

- [Programming Guide (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
