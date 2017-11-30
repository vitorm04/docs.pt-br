---
title: "Transformação funcional XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69cd09a017ab7fbf9fc56a6724abb4cc15b3e1cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="functional-transformation-of-xml-visual-basic"></a>Transformação funcional XML (Visual Basic)
Este tópico descreve a abordagem funcional pura de transformação aos documentos XML de alteração, e ele contrastes com uma abordagem procedural.  
  
## <a name="modifying-an-xml-document"></a>Alterando um documento XML  
 Uma das tarefas mais comuns para um programador XML está transformando XML de uma forma para outra. A forma de um documento XML é a estrutura do documento, que inclui o seguinte:  
  
-   A hierarquia expressa pelo documento.  
  
-   Nomes de elementos e atributos.  
  
-   Os tipos de dados de elementos e atributos.  
  
 Em geral, a abordagem mais eficiente para transformar XML de uma forma para outra é a de transformação funcional pura. Nessa abordagem, a tarefa principal do programador é criar uma transformação que é aplicada ao documento XML inteiro (ou a um ou mais nós estritamente definido). A transformação funcional é teoricamente a mais fácil de código (após um programador estiver familiarizado com a abordagem), produz o código o mais sustentável, e é geralmente mais compacta de abordagens alternativas.  
  
### <a name="xml-functional-transformational-technologies"></a>Tecnologias transformacionais funcionais XML  
 A Microsoft oferece duas tecnologias funcionais de transformação para uso em documentos XML: XSLT e LINQ to XML. XSLT é suportado no namespace gerenciada <xref:System.Xml.Xsl> e na implementação nativo COM de MSXML. Embora XSLT é uma tecnologia robusta para documentos XML de tratamento, requer a experiência em um domínio especializado, como o idioma XSLT e seus APIs de suporte.  
  
 LINQ to XML fornece as ferramentas necessárias codificação transformações e puras de uma maneira poderosa completo expressive e, em C# ou de código Visual Basic. Por exemplo, muitos dos exemplos o uso da documentação LINQ to XML uma abordagem funcional pura. Além disso, o [Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial, usamos o LINQ to XML em uma abordagem funcional para manipular as informações em um documento do Microsoft Word.  
  
 Para obter uma comparação mais completa entre LINQ to XML e outras tecnologias Microsoft XML, consulte [LINQ to XML versus Outras Tecnologias XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT a ferramenta é recomendada para transformações um documento céntricas quando o documento de origem tem uma estrutura denteada. No entanto, LINQ to XML também pode executar um documento centralizado em transformações. Para obter mais informações, consulte [como: Use anotações para transformar árvores LINQ to XML em um estilo XSLT (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução às transformações e puras (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [LINQ to XML versus Outras Tecnologias XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)  
 [LINQ to XML versus Outras Tecnologias XML](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
