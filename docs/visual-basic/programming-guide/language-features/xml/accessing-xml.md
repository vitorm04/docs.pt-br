---
title: Acessando XML no Visual Basic | Documentos do Microsoft
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 215f057f0b4d884369aad53cbbdbb98f240b56c4
ms.lasthandoff: 03/13/2017

---
# <a name="accessing-xml-in-visual-basic"></a>Acessando XML no Visual Basic
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece propriedades de eixo XML para acessar e navegar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] estruturas. Essas propriedades usam uma sintaxe especial para que você possa acessar elementos e atributos, especificando os nomes XML.  
  
 A tabela a seguir lista os recursos de linguagem que permitem que você acesse elementos e atributos no XML [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### <a name="xml-axis-properties"></a>Propriedades do eixo XML  
  
|Descrição da propriedade|Exemplo|Descrição|  
|--------------------------|-------------|-----------------|  
|*eixo filho*|`contact.<phone>`|Obtém todos os `phone` elementos que são elementos filho do `contact` elemento.|  
|*eixo de atributo*|`phone.@type`|Obtém todos os `type` atributos do `phone` elemento.|  
|*eixo descendente*|`contacts...<name>`|Obtém todos os `name` elementos do `contacts` elemento, independentemente da profundidade da hierarquia que ocorrem.|  
|*indexador de extensão*|`contacts...<name>(0)`|Obtém o primeiro `name` elemento da sequência.|  
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
  
 [Visão geral de LINQ to XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Fornece uma introdução ao uso [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] no Visual Basic.  
  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Fornece uma introdução ao uso de literais XML no Visual Basic.  
  
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Fornece links para seções sobre como carregar e modificar XML no Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Fornece links para seções que descrevem como usar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] no Visual Basic.
