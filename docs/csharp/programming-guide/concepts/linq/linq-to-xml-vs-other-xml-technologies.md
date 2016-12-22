---
title: "LINQ to XML e Outras tecnologias XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# LINQ to XML e Outras tecnologias XML
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico compara [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] às seguintes tecnologias XML: <xref:System.Xml.XmlReader>, XSLT, MSXML e XmlLite. Essas informações podem ajudá\-lo a decidir qual tecnologia usar.  
  
 Para obter uma comparação de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] para o DOM Document Object Model \(\), consulte [LINQ to XML e DOM \(C\#\)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## LINQ to XML e XmlReader  
 <xref:System.Xml.XmlReader> é um analisador rápido, somente de encaminhamento e sem cache.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é implementado na parte superior do <xref:System.Xml.XmlReader>, e eles são totalmente integrados. No entanto, você também pode usar <xref:System.Xml.XmlReader> por si só.  
  
 Por exemplo, suponha que você está criando um serviço Web que analisará centenas de documentos XML por segundo e os documentos terá a mesma estrutura, que significa que você só precisa escrever uma implementação de código para analisar o XML. Nesse caso, você provavelmente desejaria usar <xref:System.Xml.XmlReader> por si só.  
  
 Por outro lado, se você estiver criando um sistema que analisa vários documentos XML menores, e cada um deles é diferente, convém aproveitar as melhorias de produtividade que [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] fornece.  
  
## LINQ to XML e XSLT  
 Ambos [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] e XSLT fornecem recursos abrangentes de transformação de documento XML. O XSLT é uma abordagem declarativa baseada em regras. Avançado XSLT programadores escrever XSLT em um estilo de programação funcional que enfatiza uma abordagem sem monitoração de estado. As transformações podem ser escritas usando funções puras que são implementadas sem efeitos colaterais. Essa abordagem baseada em regras ou funcional é desconhecida para muitos desenvolvedores e pode ser difícil e demorada.  
  
 XSLT pode ser um sistema muito produtivo que gera aplicativos de alto desempenho. Por exemplo, algumas grandes empresas da Web usam XSLT como uma maneira de gerar HTML de XML que foi retirado de uma variedade de armazenamentos de dados. O mecanismo XSLT gerenciado compila XSLT em código CLR e executa melhor em alguns cenários em que o mecanismo XSLT nativo.  
  
 No entanto, XSLT não aproveita o conhecimento de c\# e Visual Basic que muitos desenvolvedores têm. Ele exige que os desenvolvedores escrever código em uma linguagem de programação diferente e complexa. Usando dois sistemas de desenvolvimento não integrados, como c\# \(ou Visual Basic\) e XSLT, resulta em sistemas de software que são mais difíceis de desenvolver e manter.  
  
 Após você dominar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] expressões de consulta [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] transformações são uma tecnologia poderosa que é fácil de usar. Basicamente, você forma seu documento XML usando construção funcional, extraindo dados de várias fontes, construindo <xref:System.Xml.Linq.XElement> objetos dinamicamente e montando o todo em uma nova árvore XML. A transformação pode gerar um documento completamente novo. Construir transformações no [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é relativamente fácil e intuitivo, e o código resultante é legível. Isso reduz os custos de desenvolvimento e manutenção.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] não se destina a substituir o XSLT. XSLT ainda é a ferramenta de escolha para transformações XML complicadas e centrados em documentos, especialmente se a estrutura do documento não é bem definida.  
  
 O XSLT tem a vantagem de ser um World Wide Web Consortium \(W3C\) padrão. Se você tiver um requisito para usar somente as tecnologias são padrões, o XSLT pode ser mais apropriado.  
  
 XSLT é XML e, portanto, pode ser manipulado programaticamente.  
  
## LINQ to XML e MSXML  
 MSXML é a tecnologia baseada em COM para processar XML que está incluído no Microsoft Windows. O MSXML fornece uma implementação nativa do DOM com suporte para XPath e XSLT. Ele também contém o analisador do SAX2 não cache, com base em eventos.  
  
 MSXML funciona bem, é seguro por padrão na maioria dos cenários e pode ser acessado no Internet Explorer para executar processamento em aplicativos de estilo AJAX de XML do lado do cliente. O MSXML pode ser usado em qualquer linguagem de programação que dá suporte a COM, incluindo C\+\+, JavaScript e [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0.  
  
 O MSXML não é recomendado para uso em código gerenciado com base no common language runtime \(CLR\).  
  
## LINQ to XML e XmlLite  
 O XmlLite é não cache, para frente, analisador de pull. Os desenvolvedores usam XmlLite principalmente com C\+\+. Ele não é recomendado para os desenvolvedores usem XmlLite com código gerenciado.  
  
 A principal vantagem de XmlLite é que ele é um analisador XML leve e rápido seguro na maioria dos cenários. Sua área de superfície de ameaças é muito pequena. Se você precisar analisar documentos não confiáveis e você deseja proteger contra ataques, como negação de serviço ou exposição de dados, XmlLite pode ser uma boa opção.  
  
 O XmlLite não está integrado com [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]. Não produz o programador melhorias de produtividade que são a força motriz associada [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  
  
## Consulte também  
 [Guia de introdução \(LINQ to XML\)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)