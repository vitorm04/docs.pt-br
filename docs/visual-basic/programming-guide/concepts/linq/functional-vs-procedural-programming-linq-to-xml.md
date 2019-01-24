---
title: Programação funcional versus Programação procedural (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: d5db2f686d72390cdb7e338235a39e4039281e6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644996"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a>Programação funcional versus Programação procedural (LINQ to XML) (Visual Basic)
Há vários tipos de aplicativos XML:  
  
-   Alguns aplicativos utilizam documentos XML de origem e geram novos documentos XML que estão em um formato diferente do que os documentos de origem.  
  
-   Alguns aplicativos utilizam documentos XML de origem e produzem documentos de resultado em um formato totalmente diferente, como arquivos de texto HTML ou CSV.  
  
-   Alguns aplicativos utilizam documentos XML de origem e inserem registros em um banco de dados.  
  
-   Alguns aplicativos utilizam dados de outra origem, como um banco de dados e criam documentos XML a partir deles.  
  
 Esses não são todos os tipos de aplicativos XML, mas são um conjunto representativo de tipos de funcionalidade que um programador XML tem que implementar.  
  
 Com todos esses tipos de aplicativos, há duas abordagens contrastantes que um desenvolvedor pode utilizar:  
  
-   Construção funcional usando uma abordagem declarativa.  
  
-   Modificação da árvore XML na memória usando código procedural.  
  
 O LINQ to XML oferece suporte às duas abordagens.  
  
 Ao usar a abordagem funcional, você escreve as transformações que utilizam os documentos de origem e geram documentos de resultado completamente novos com o formato desejado.  
  
 Ao modificar uma árvore XML no lugar, você escreve o código que percorre e navega por meio de nós em uma árvore XML na memória, inserindo, excluindo e modificando os nós conforme o necessário.  
  
 Você pode usar LINQ to XML com qualquer abordagem. Você usa as mesmas classes e, em alguns casos, os mesmos métodos. No entanto, a estrutura e as metas das duas abordagens são muito diferentes. Por exemplo, em situações diferentes, uma ou outra abordagem terá geralmente melhor desempenho, e usará mais ou menos memória. Além disso, uma ou outra abordagem será mais fácil de escrever e produzirá um código mais sustentável.  
  
 Para ver as duas abordagens contrastadas, consulte [Modificação de árvore XML na memória versus Construção funcional (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).  
  
 Para obter um tutorial sobre como escrever transformações funcionais, consulte [transformações funcionais puras de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Consulte também
- [LINQ to XML visão geral da programação (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
