---
title: Visão geral dos literais XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: 4024f4ad2b2aa8cb1897e83d87a7a00b1ba25e67
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964701"
---
# <a name="xml-literals-overview-visual-basic"></a>Visão geral dos literais XML (Visual Basic)
Um *literal XML* permite que você incorpore XML diretamente em seu código de Visual Basic. A sintaxe XML literal representa [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos, e é semelhante à sintaxe XML 1,0. Isso facilita a criação de elementos e documentos XML programaticamente porque seu código tem a mesma estrutura que o XML final.  
  
 Visual Basic compila literais XML em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]fornece um modelo de objeto simples para criar e manipular XML, e esse modelo se integra bem com [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]o. Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.  
  
 Você pode inserir uma expressão de Visual Basic em um literal XML. Em tempo de execução, seu aplicativo cria [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] um objeto para cada literal, incorporando os valores das expressões inseridas. Isso permite que você especifique o conteúdo dinâmico dentro de um literal XML. Para obter mais informações, consulte [expressões inseridas em XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Para obter mais informações sobre as diferenças entre a sintaxe XML literal e a sintaxe XML 1,0, consulte [literais XML e a especificação xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Literais simples  
 Você pode criar um [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto em seu código de Visual Basic digitando ou colando em XML válido. Um literal de elemento XML retorna <xref:System.Xml.Linq.XElement> um objeto. Para obter mais informações, consulte [literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) e [literais XML e a especificação XML 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). O exemplo a seguir cria um elemento XML que tem vários elementos filho.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Você pode criar um documento XML iniciando um literal XML com `<?xml version="1.0"?>`, conforme mostrado no exemplo a seguir. Um literal de documento XML retorna <xref:System.Xml.Linq.XDocument> um objeto. Para obter mais informações, consulte [literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> A sintaxe XML literal em Visual Basic não é idêntica à sintaxe na especificação XML 1,0. Para obter mais informações, consulte [literais XML e a especificação xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Continuação de linha  
 Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha (a sequência espaço sublinhado-inserir). Isso facilita a comparação de literais XML no código com documentos XML.  
  
 O compilador trata os caracteres de continuação de linha como parte de um literal XML. Portanto, você deve usar a sequência espaço sublinhado-inserir somente quando ela pertence [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ao objeto.  
  
 No entanto, você precisará de caracteres de continuação de linha se tiver uma expressão de várias linhas em uma expressão inserida. Para obter mais informações, consulte [expressões inseridas em XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Inserindo consultas em literais XML  
 Você pode usar uma consulta em uma expressão inserida. Quando você faz isso, os elementos retornados pela consulta são adicionados ao elemento XML. Isso permite que você adicione conteúdo dinâmico, como o resultado de uma consulta de usuário, a um literal XML.  
  
 Por exemplo, o código a seguir usa uma consulta inserida para criar elementos XML a partir dos `phoneNumbers2` membros da matriz e, em seguida, adicionar `contact2`esses elementos como filhos de.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Como o compilador cria objetos a partir de literais XML  
 O compilador Visual Basic converte literais XML em chamadas para os construtores equivalentes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] para criar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto. Por exemplo, o compilador Visual Basic converterá o exemplo de código a seguir em uma chamada <xref:System.Xml.Linq.XProcessingInstruction> para o construtor para a instrução de versão XML, <xref:System.Xml.Linq.XElement> chamadas para o `<contact>`Construtor `<name>`para o `<phone>` , e elementos e chamadas para o <xref:System.Xml.Linq.XAttribute> Construtor `type` do atributo. Especificamente, considerando os atributos no exemplo a seguir, o compilador Visual Basic chamará o <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> Construtor duas vezes. O primeiro passará o valor `type` para o `name` parâmetro e o valor `home` para o `value` parâmetro. O segundo também passará o valor `type` para o `name` parâmetro, mas o valor `work` para o `value` parâmetro.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement>
- [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Expressões Inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Literal de Documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literal do Elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md)
