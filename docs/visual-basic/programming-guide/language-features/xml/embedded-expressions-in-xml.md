---
title: Expressões inseridas no XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: ef8ac62d9d969ce4463931d69b0302376ca0ccc4
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881536"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Expressões inseridas no XML (Visual Basic)
Expressões inseridas permitem criar literais XML que contêm expressões que são avaliadas em tempo de execução. É a sintaxe para uma expressão inserida `<%=` `expression` `%>`, que é o mesmo que a sintaxe usada no ASP.NET.  
  
 Por exemplo, você pode criar um elemento XML literal, combinar expressões inseridas com o conteúdo de texto literal.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 Se `isbnNumber` contém o número inteiro 12345 e `modifiedDate` contém a data 3/5/2006, quando esse código é executado, o valor de `book` é:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Validação e o local de expressão incorporada  
 Expressões inseridas podem aparecer somente em determinados locais dentro de expressões literais do XML. Os controles de localização de expressão que tipos de expressão podem retornar e como `Nothing` é tratada. A tabela a seguir descreve os locais permitidos e os tipos de expressões inseridas.  
  
|Local no literal|Tipo de expressão|Tratamento de `Nothing`|  
|---|---|---|  
|Nome do elemento XML|<xref:System.Xml.Linq.XName>|Erro|  
|Conteúdo do elemento XML|`Object` ou uma matriz de `Object`|Ignorado|  
|Nome de atributo do elemento XML|<xref:System.Xml.Linq.XName>|Erro, a menos que o valor de atributo também é `Nothing`|  
|Valor de atributo do elemento XML|`Object`|Declaração de atributo ignorada|  
|Atributo de elemento XML|<xref:System.Xml.Linq.XAttribute> ou uma coleção de <xref:System.Xml.Linq.XAttribute>|Ignorado|  
|Elemento de raiz do documento XML|<xref:System.Xml.Linq.XElement> ou uma coleção de um <xref:System.Xml.Linq.XElement> objeto e um número arbitrário de <xref:System.Xml.Linq.XProcessingInstruction> e <xref:System.Xml.Linq.XComment> objetos|Ignorado|  
  
- Exemplo de uma expressão inserida em um nome de elemento XML:  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- Exemplo de uma expressão inserida no conteúdo de um elemento XML:  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- Exemplo de uma expressão inserida em um nome de atributo do elemento XML:  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- Exemplo de uma expressão inserida em um valor de atributo do elemento XML:  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- Exemplo de uma expressão inserida em um atributo de elemento XML:  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- Exemplo de uma expressão inserida em um elemento de raiz do documento XML:  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 Se você habilitar `Option Strict`, o compilador verifica que o tipo de cada expressão inserida é ampliado para o tipo solicitado. A única exceção é para o elemento raiz de um documento XML, que é verificado quando o código é executado. Se você compilar sem `Option Strict`, você pode inserir expressões do tipo `Object` e seu tipo é verificado em tempo de execução.  
  
 Em locais onde o conteúdo é opcional, que contêm expressões incorporadas `Nothing` são ignorados. Isso significa que você não precisa verificar o conteúdo de elemento, valores de atributo, e elementos de matriz não são `Nothing` antes de usar um literal XML. Necessário valores, como nomes de elementos e atributos, não podem ser `Nothing`.  
  
 Para obter mais informações sobre como usar uma expressão inserida em um determinado tipo de literal, consulte [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Regras de escopo  
 O compilador converte cada literal XML em uma chamada de construtor para o tipo de literal apropriado. O conteúdo literal e expressões incorporadas em um literal XML são passadas como argumentos para o construtor. Isso significa que todos os Visual Basic elementos de programação disponíveis para um literal XML também estão disponíveis para suas expressões inseridas.  
  
 Um literal XML, você pode acessar o namespace XML prefixos declarados com o `Imports` instrução. Você pode declarar um novo prefixo de namespace XML ou um prefixo de namespace XML existente, em um elemento por meio de sombra a `xmlns` atributo. O novo namespace está disponível para os nós filho desse elemento, mas não para literais XML em expressões inseridas.  
  
> [!NOTE]
>  Quando você declara um prefixo de namespace XML usando o `xmlns` atributo namespace, o valor do atributo deve ser uma cadeia de caracteres constante. Nesse sentido, usando o `xmlns` atributo é como usar o `Imports` declaração para declarar um namespace de XML. Você não pode usar uma expressão inserida para especificar o valor de namespace XML.  
  
## <a name="see-also"></a>Consulte também

- [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literal de Documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literal do Elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Instrução Imports (Tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Visão Geral dos Literais XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
