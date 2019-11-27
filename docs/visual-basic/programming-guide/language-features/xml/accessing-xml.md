---
title: Acessar XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 1fa1d94fc710272ac0ba9ea7167989da42a51fcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351742"
---
# <a name="accessing-xml-in-visual-basic"></a>Acessando XML no Visual Basic
Visual Basic fornece propriedades de eixo XML para acessar e navegar em estruturas de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Essas propriedades usam uma sintaxe especial para permitir que você acesse elementos e atributos especificando os nomes XML.  
  
 A tabela a seguir lista os recursos de linguagem que permitem acessar elementos e atributos XML no Visual Basic.  
  
### <a name="xml-axis-properties"></a>Propriedades do eixo XML  
  
|Descrição da propriedade|Exemplo|Descrição|  
|--------------------------|-------------|-----------------|  
|*eixo filho*|`contact.<phone>`|Obtém todos os elementos de `phone` que são elementos filho do elemento `contact`.|  
|*eixo de atributo*|`phone.@type`|Obtém todos os atributos de `type` do elemento `phone`.|  
|*eixo descendente*|`contacts...<name>`|Obtém todos os elementos `name` do elemento `contacts`, independentemente da profundidade na hierarquia que eles ocorrem.|  
|*indexador de extensão*|`contacts...<name>(0)`|Obtém o primeiro elemento `name` da sequência.|  
|*value*|`contacts...<name>.Value`|Obtém a representação da cadeia de caracteres do primeiro objeto na sequência, ou `Nothing` se a sequência estiver vazia.|  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como acessar elementos descendentes XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidos em um elemento XML especificado.  
  
 [Como acessar elementos filho XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Mostra como usar uma propriedade de eixo filho para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.  
  
 [Como acessar atributos XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Mostra como usar uma propriedade de eixo de atributo para acessar todos os atributos XML que têm um nome especificado em um elemento XML.  
  
 [Como declarar e usar prefixos de namespace de XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Mostra como declarar um prefixo de namespace XML e usá-lo para criar e acessar elementos XML.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Propriedades do Eixo XML](../../../../visual-basic/language-reference/xml-axis/index.md)  
 Fornece links para seções que descrevem as várias propriedades de acesso de XML.  
  
 [Visão geral do LINQ to XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Fornece uma introdução ao uso de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] no Visual Basic.  
  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Fornece uma introdução ao uso de literais XML no Visual Basic.  
  
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Fornece links para seções sobre como carregar e modificar XML no Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Fornece links para seções que descrevem como usar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] no Visual Basic.
