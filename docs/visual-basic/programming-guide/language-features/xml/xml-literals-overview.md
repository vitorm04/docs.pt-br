---
title: "Visão geral dos literais XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59ce79995025692428263120f9c21c7baf5cf231
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-literals-overview-visual-basic"></a>Visão geral dos literais XML (Visual Basic)
Um *literal XML* permite incorporar XML diretamente no seu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] código. A sintaxe de literais XML representa [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos e é semelhante à sintaxe XML 1.0. Isso torna mais fácil criar elementos XML e documentos programaticamente porque seu código tem a mesma estrutura que o XML final.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]compila literais XML em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Fornece um modelo de objeto simples para criar e manipular XML e esse modelo integra bem com [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.  
  
 Você pode inserir um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] expressão em um literal XML. Em tempo de execução, seu aplicativo cria um [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto para cada literal, incorporando os valores das expressões incorporadas. Isso lhe permite especificar o conteúdo dinâmico dentro de um literal XML. Para obter mais informações, consulte [expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Para obter mais informações sobre as diferenças entre a sintaxe de literais XML e a sintaxe do XML 1.0, consulte [literais XML e a especificação do XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Literais simples  
 Você pode criar um [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do objeto em seu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] código digitando ou colando XML válido. Um literal de elemento XML retorna um <xref:System.Xml.Linq.XElement> objeto. Para obter mais informações, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) e [literais XML e a especificação do XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). O exemplo a seguir cria um elemento XML que tem vários elementos filhos.  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 Você pode criar um documento XML iniciando um literal XML com `<?xml version="1.0"?>`, conforme mostrado no exemplo a seguir. Um documento XML retorna um <xref:System.Xml.Linq.XDocument> objeto. Para obter mais informações, consulte [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  A sintaxe de literais de XML em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não é idêntica à sintaxe na especificação XML 1.0. Para obter mais informações, consulte [literais XML e a especificação do XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Continuação de linha  
 Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha (a sequência de espaço-sublinhado-enter). Isso torna mais fácil comparar literais XML no código com documentos XML.  
  
 O compilador trata caracteres de continuação de linha como parte de um literal XML. Portanto, você deve usar a sequência de espaço-sublinhado-enter apenas quando ele pertence a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto.  
  
 No entanto, você precisa de caracteres de continuação de linha se você tiver uma expressão de várias linhas em uma expressão inserida. Para obter mais informações, consulte [expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Inserindo consultas em literais XML  
 Você pode usar uma consulta em uma expressão inserida. Quando você fizer isso, os elementos retornados pela consulta são adicionados ao elemento XML. Isso permite adicionar conteúdo dinâmico, como o resultado da consulta do usuário, para um literal XML.  
  
 Por exemplo, o código a seguir usa uma consulta incorporada para criar elementos XML dos membros do `phoneNumbers2` de matriz e, em seguida, adiciona esses elementos como filhos do `contact2`.  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Como o compilador cria objetos de literais XML  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte literais XML em chamadas para o equivalente [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] construtores para criar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto. Por exemplo, o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converterá o exemplo de código a seguir em uma chamada para o <xref:System.Xml.Linq.XProcessingInstruction> construtor para a instrução da versão XML, chamadas para o <xref:System.Xml.Linq.XElement> construtor para o `<contact>`, `<name>`e `<phone>`elementos e chamadas para o <xref:System.Xml.Linq.XAttribute> construtor para o `type` atributo. Especificamente, dados os atributos no exemplo a seguir, o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador chamará o <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> construtor duas vezes. O primeiro irá passar o valor `type` para o `name` parâmetro e o valor `home` para o `value` parâmetro. O segundo irá passar o valor `type` para o `name` parâmetro, mas o valor `work` para o `value` parâmetro.  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Expressões Inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Literal de Documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Literal do Elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md)
