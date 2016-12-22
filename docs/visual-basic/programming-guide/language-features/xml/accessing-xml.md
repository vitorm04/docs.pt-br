---
title: "Acessando XML no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "acessando XML [Visual Basic], propriedades do eixo"
  - "LINQ to XML [Visual Basic], acessando XML"
  - "código do Visual Basic, XML"
  - "XML [Visual Basic], acessando"
  - "XML [Visual Basic], propriedades do eixo"
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Acessando XML no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece propriedades de eixo XML para acessar e navegar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] estruturas.  Essas propriedades usam uma sintaxe especial para que você possa acessar os elementos e atributos, especificando os nomes XML.  
  
 A tabela a seguir lista os recursos de linguagem que permitem que você acesse os elementos XML e atributos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### Propriedades do eixo XML  
  
|Descrição da propriedade|Exemplo|Descrição|  
|------------------------------|-------------|---------------|  
|*eixo filho*|`contact.<phone>`|Obtém todos os `phone` elementos que são elementos filho da `contact` elemento.|  
|*eixo de atributo*|`phone.@type`|Obtém todos os `type` atributos da `phone` elemento.|  
|*eixo descendente*|`contacts...<name>`|Obtém todos os `name` elementos da `contacts` elemento, independentemente de como profundidade na hierarquia que eles ocorram.|  
|*Indexador de extensão*|`contacts...<name>(0)`|Obtém o primeiro `name` elemento da seqüência.|  
|*Valor*|`contacts...<name>.Value`|Obtém a representação de seqüência de caracteres do primeiro objeto na seqüência, ou `Nothing` se a seqüência estiver vazia.|  
  
## Nesta seção  
 [Como acessar elementos descendentes XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Mostra como usar uma propriedade do eixo descendente para acessar todos os elementos XML que possuem um nome especificado e que estão contidas em um elemento especificado XML.  
  
 [Como acessar elementos filho XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Mostra como usar um propriedade do eixo filho para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.  
  
 [Como acessar atributos XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Mostra como usar um propriedade do eixo de atributo para acessar todos os atributos XML que têm um nome especificado em um elemento XML.  
  
 [Como declarar e usar prefixos de namespace XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Mostra como declarar um prefixo namespace para XML e usá\-lo para criar e acessar elementos XML.  
  
## Seções relacionadas  
 [Propriedades do eixo XML](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 Fornece links para seções que descrevem as diversas propriedades de acesso do XML.  
  
 [Visão geral de LINQ to XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Fornece uma introdução ao uso [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] em Visual Basic.  
  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Fornece uma introdução ao uso de literais XML no Visual Basic.  
  
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Fornece links para seções sobre como carregar e modificar o XML no Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Fornece links para seções que descrevem como usar o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] em Visual Basic.