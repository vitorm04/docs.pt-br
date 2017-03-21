---
title: LINQ to XML e Outros Technologies2 XML | Documentos do Microsoft
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
ms.assetid: 72ce3a82-ffc6-488c-98e7-b9b40f3591ec
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
ms.openlocfilehash: 0254788fb9efa018e735a57990144c6b176d30d6
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML e Outras tecnologias XML
Este tópico compara [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] para as seguintes tecnologias XML: <xref:System.Xml.XmlReader>, XSLT, MSXML e XmlLite.</xref:System.Xml.XmlReader> Estas informações podem ajudá-lo a decidir qual tecnologia usar.  
  
 Para obter uma comparação de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] para o DOM Document Object Model (), consulte [LINQ to XML e. DOM (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML e XmlReader  
 <xref:System.Xml.XmlReader>é um analisador rápido, somente de encaminhamento e sem cache.</xref:System.Xml.XmlReader>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]é implementado na parte superior do <xref:System.Xml.XmlReader>, e eles são totalmente integrados.</xref:System.Xml.XmlReader> No entanto, você também pode usar <xref:System.Xml.XmlReader>por si só.</xref:System.Xml.XmlReader>  
  
 Por exemplo, suponha que você esteja criando um serviço Web que analisará centenas de documentos XML por segundo e que os documentos tenham a mesma estrutura, o que significa que você só precisará criar uma única implementação do código para analisar o XML. Nesse caso, você provavelmente desejaria usar <xref:System.Xml.XmlReader>por si só.</xref:System.Xml.XmlReader>  
  
 Por outro lado, se você estiver criando um sistema que analisa vários documentos XML menores, e cada um deles é diferente, convém aproveitar as melhorias de produtividade que [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] fornece.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML e XSLT  
 Ambos [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] e XSLT fornecem recursos abrangentes de transformação de documento XML. A linguagem XSLT é uma abordagem declarativa baseada em regras. Programadores avançados de XSLT criam XSLT em um estilo funcional de programação que enfatiza uma abordagem sem estado. As transformações podem ser criadas com o uso de funções puras que são implementadas sem efeitos colaterais. Essa abordagem funcional baseada em regras é desconhecida para muitos desenvolvedores e sua compreensão pode ser difícil e demorada.  
  
 A linguagem XSLT pode ser um sistema muito produtivo que gera aplicativos de alto desempenho. Por exemplo, algumas grandes empresas da Web usam XSLT para gerar HTML de XML extraído de uma variedade de repositórios de dados. O mecanismo XSLT gerenciado compila XSLT em código CLR e é executado ainda melhor em alguns cenários do que o mecanismo XSLT nativo.  
  
 No entanto, XSLT não aproveita as vantagens dos conhecimentos de C# e de Visual Basic que muitos desenvolvedores possuem. Ela requer que os desenvolvedores criem código em uma linguagem de programação diferente e complexa. O uso de dois sistemas de desenvolvimento não integrados, como C# (ou Visual Basic) e XSLT, resulta em sistemas de software que são mais difíceis de desenvolver e manter.  
  
 Após você dominar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] expressões de consulta [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] transformações são uma tecnologia poderosa que é fácil de usar. Basicamente, você forma seu documento XML usando construção funcional, extraindo dados de várias fontes, construindo <xref:System.Xml.Linq.XElement>objetos dinamicamente e montando o todo em uma nova árvore XML.</xref:System.Xml.Linq.XElement> A transformação pode gerar um documento completamente novo. Construir transformações no [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é relativamente fácil e intuitivo, e o código resultante é legível. Isso reduz custos de desenvolvimento e de manutenção.  
  
 O [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] não pretende substituir a linguagem XSLT. A linguagem XSLT ainda é a melhor ferramenta para transformações XML complicadas e centradas em documentos, especialmente se a estrutura do documento não estiver bem-definida.  
  
 A linguagem XSLT tem a vantagem de ser um padrão W3C (World Wide Web Consortium). Se você tiver um requisito de usar apenas tecnologias que sejam padrões, a linguagem XSLT pode ser mais apropriada.  
  
 XSLT é XML; portanto, ela pode ser manipulada programaticamente.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML e MSXML  
 MSXML é a tecnologia baseada em COM para processar XML que vem incluída no Microsoft Windows. A tecnologia MSXML fornece uma implementação nativa do DOM com suporte para XPath e XSLT. Ela também contém o analisador SAX2 baseado em eventos e não armazenado em cache.  
  
 A MSXML tem bom desempenho, é segura por padrão na maioria dos cenários e pode ser acessada no Internet Explorer para executar processamento XML do lado do cliente em aplicativos em estilo AJAX. A MSXML pode ser usada de qualquer linguagem de programação que dê suporte a COM, incluindo C++, JavaScript e [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0.  
  
 A MSXML não é recomendada para uso em código gerenciado baseado em CLR (Common Language Runtime).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML e XmlLite  
 XmlLite é um analisador de pull, somente encaminhamento e não armazenado em cache. Os desenvolvedores usam XmlLite principalmente com C++. Não é recomendado que os desenvolvedores usem XmlLite com código gerenciado.  
  
 A principal vantagem de XmlLite é ser um analisador XML leve, rápido e seguro na maioria dos cenários. Sua área de superfície de ameaças é muito pequena. Se você precisar analisar documentos não confiáveis e quiser protegê-los contra ataques de negação de serviço ou da exibição de dados, XmlLite pode ser uma boa opção.  
  
 XmlLite não está integrado com [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]. Não produz o programador melhorias de produtividade que são a força motriz associada [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Introdução (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
