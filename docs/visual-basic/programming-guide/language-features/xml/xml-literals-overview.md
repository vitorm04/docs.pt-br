---
title: "Visão geral dos literais XML (Visual Basic) | Documentos do Microsoft"
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
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 57d036910ba9e49385caca28de222a8a8e28ec56
ms.lasthandoff: 03/13/2017

---
# <a name="xml-literals-overview-visual-basic"></a>Visão geral dos literais XML (Visual Basic)
Um *literal XML* permite incorporar XML diretamente no seu [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código. A sintaxe literal XML representa [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objetos e é semelhante à sintaxe XML 1.0. Isso facilita criar elementos XML e documentos por meio de programação porque seu código possui a mesma estrutura que o XML final.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]compila literais XML em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objetos. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Fornece um modelo de objeto simples para criar e manipular XML e esse modelo integra bem com [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]. Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>  
  
 Você pode incorporar um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] expressão em um literal XML. Em tempo de execução, seu aplicativo cria um [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objeto para cada literal, incorporando os valores das expressões incorporadas. Isso permite que você especifique conteúdo dinâmico dentro um literal XML. Para obter mais informações, consulte [expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Para obter mais informações sobre as diferenças entre a sintaxe de literais XML e a sintaxe XML 1.0, consulte [literais XML e a especificação do XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Literais simples  
 Você pode criar um [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] o objeto no seu [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código digitando ou colando XML válido. Um literal de elemento XML retorna um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement> Para obter mais informações, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) e [literais XML e a especificação do XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). O exemplo a seguir cria um elemento XML que tem vários elementos filhos.  
  
 [!code-vb[VbXMLSamples n º&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 Você pode criar um documento XML iniciando um literal XML com `<?xml version="1.0"?>`, conforme mostrado no exemplo a seguir. Um documento XML retorna um <xref:System.Xml.Linq.XDocument>objeto.</xref:System.Xml.Linq.XDocument> Para obter mais informações, consulte [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples n º&6;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  A sintaxe de literais XML em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não é idêntica à sintaxe na especificação XML 1.0. Para obter mais informações, consulte [literais XML e a especificação do XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Continuação de linha  
 Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha (a sequência de espaço-sublinhado-enter). Isso facilita a comparar literais XML no código com documentos XML.  
  
 O compilador trata caracteres de continuação de linha como parte de uma literal XML. Portanto, você deve usar a sequência de espaço-sublinhado-enter apenas quando ele pertence a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objeto.  
  
 No entanto, você precisa de caracteres de continuação de linha se você tiver uma expressão de várias linhas em uma expressão inserida. Para obter mais informações, consulte [expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Inserindo consultas em literais XML  
 Você pode usar uma consulta em uma expressão inserida. Quando você fizer isso, os elementos retornados pela consulta são adicionados ao elemento XML. Isso permite que você adicionar conteúdo dinâmico, como o resultado da consulta do usuário, para um literal XML.  
  
 Por exemplo, o código a seguir usa uma consulta incorporada para criar elementos XML a partir dos membros do `phoneNumbers2` de matriz e, em seguida, adiciona esses elementos como filhos do `contact2`.  
  
 [!code-vb[VbXMLSamples&#7;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Como o compilador cria objetos de literais XML  
 O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte literais XML em chamadas para o equivalente [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] construtores para criar o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objeto. Por exemplo, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converterá o seguinte exemplo de código em uma chamada para o <xref:System.Xml.Linq.XProcessingInstruction>construtor para a instrução da versão XML, chamadas para o <xref:System.Xml.Linq.XElement>construtor para o `<contact>`, `<name>`, e `<phone>` elementos e chamadas para o <xref:System.Xml.Linq.XAttribute>construtor para o `type` atributo.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XProcessingInstruction> Especificamente, dados os atributos no exemplo a seguir, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador chamará o <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>construtor duas vezes.</xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> O primeiro irá passar o valor `type` para o `name` parâmetro e o valor `home` para o `value` parâmetro. O segundo irá passar o valor `type` para o `name` parâmetro, mas o valor `work` para o `value` parâmetro.  
  
 [!code-vb[VbXMLSamples n º&6;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>   
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md)
