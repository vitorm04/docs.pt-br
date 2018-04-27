---
title: Eixos LINQ to XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 404ddcc89e6549d7575761e10c23413d9688a38f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-xml-axes-visual-basic"></a>Eixos LINQ to XML (Visual Basic)
Após criar uma árvore XML ou carregar um documento XML em uma árvore XML, você poderá consultá-la para localizar elementos e atributos, e recuperar seus valores.  
  
 Antes de poder criar consultas, você deve entender os eixos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Há dois tipos de métodos de eixo: primeiro, existem métodos que você chama em um único objeto <xref:System.Xml.Linq.XElement>, objeto <xref:System.Xml.Linq.XDocument> ou objeto <xref:System.Xml.Linq.XNode>. Esses métodos operam em um único objeto e retornam uma coleção de objetos <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute> ou <xref:System.Xml.Linq.XNode>. Segundo, existem métodos de extensão que operam em coleções e retornam coleções. Os métodos de extensão enumeram a coleção de origem, chamam o método de eixo apropriado em cada item na coleção e concatenam os resultados.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[LINQ para visão geral de eixos XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Define os eixos e explica como eles são usados no contexto de consultas [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Como: recuperar uma coleção de elementos (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Apresenta o método <xref:System.Xml.Linq.XContainer.Elements%2A>. Esse método retorna uma coleção de elementos filho de um elemento.|  
|[Como: recuperar o valor de um elemento (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Mostra como obter os valores de elementos.|  
|[Como: Filtrar em nomes de elemento (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Mostra como filtrar em nomes de elementos ao usar eixos.|  
|[Como: encadear chamadas de método do eixo (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Mostra como encadear chamadas a métodos de eixos.|  
|[Como: recuperar um único elemento filho (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Mostra como recuperar um único elemento filho de um elemento, dado o nome da marca do elemento filho.|  
|[Como: recuperar uma coleção de atributos (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Apresenta o método <xref:System.Xml.Linq.XElement.Attributes%2A>. Esse método recupera os atributos de um elemento.|  
|[Como: recuperar um único atributo (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Mostra como recuperar um único atributo de um elemento, dado o nome do atributo.|  
|[Como: recuperar o valor de um atributo (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Mostra como obter os valores de atributos.|  
|[Como: recuperar o valor raso de um elemento (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Mostra como recuperar o valor superficial de um elemento.|  
|[Eixos linguagem integrados em Visual Basic (LINQ para XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Resume os eixos integrado do Visual Basic.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de programação (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
