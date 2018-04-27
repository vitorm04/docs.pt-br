---
title: Acessando XML no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 064e4b224d37172b8f79e57c73164b90186ef922
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="accessing-xml-in-visual-basic"></a>Acessando XML no Visual Basic
Visual Basic fornece propriedades de eixo XML para acessar e navegar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] estruturas. Essas propriedades usam uma sintaxe especial para que você possa acessar os elementos e atributos, especificando os nomes XML.  
  
 A tabela a seguir lista os recursos de linguagem que permitem acessar elementos XML e atributos no Visual Basic.  
  
### <a name="xml-axis-properties"></a>Propriedades do eixo XML  
  
|Descrição da propriedade|Exemplo|Descrição|  
|--------------------------|-------------|-----------------|  
|*eixo filho*|`contact.<phone>`|Obtém todos os `phone` elementos que são elementos filho do `contact` elemento.|  
|*eixo de atributo*|`phone.@type`|Obtém todos os `type` atributos do `phone` elemento.|  
|*eixo descendente*|`contacts...<name>`|Obtém todos os `name` elementos do `contacts` elemento, independentemente da profundidade da hierarquia que eles ocorrem.|  
|*indexador de extensão*|`contacts...<name>(0)`|Obtém a primeira `name` elemento da sequência.|  
|*value*|`contacts...<name>.Value`|Obtém a representação de cadeia de caracteres do primeiro objeto na sequência, ou `Nothing` se a sequência for vazia.|  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como acessar elementos descendentes XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidas em um elemento XML especificado.  
  
 [Como acessar elementos filho XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Mostra como usar um filho propriedade de eixo para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.  
  
 [Como acessar atributos XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Mostra como usar uma propriedade de eixo de atributo para acessar todos os atributos XML que têm um nome especificado em um elemento XML.  
  
 [Como declarar e usar prefixos de namespace de XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Mostra como declarar um prefixo de namespace XML e usá-lo para criar e acessar elementos XML.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Propriedades do Eixo XML](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 Fornece links para seções que descrevem as várias propriedades de acesso do XML.  
  
 [Visão geral do LINQ to XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Fornece uma introdução ao uso [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] no Visual Basic.  
  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Fornece uma introdução ao uso de literais XML no Visual Basic.  
  
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Fornece links para seções sobre como carregar e modificar o XML no Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Fornece links para seções que descrevem como usar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] no Visual Basic.
