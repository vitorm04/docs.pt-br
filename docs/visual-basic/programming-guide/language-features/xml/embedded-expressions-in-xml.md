---
title: "Expressões incorporadas no XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
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
ms.openlocfilehash: e5cd40e55ec23de3ad1bb2f5f065762c893d9cb3
ms.lasthandoff: 03/13/2017

---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Expressões inseridas no XML (Visual Basic)
Expressões inseridas permitem criar literais XML que contêm expressões que são avaliadas em tempo de execução. A sintaxe para uma expressão inserida é `<%=` `expression` `%>`, que é a mesma que a sintaxe utilizada no [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].  
  
 Por exemplo, você pode criar um elemento XML literal, combinar expressões inseridas com conteúdo de texto literal.  
  
 [!code-vb[VbXMLSamples&#27;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 Se `isbnNumber` contém o número inteiro 12345 e `modifiedDate` contém a data 3/5/2006, quando esse código é executado, o valor de `book` é:  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Validação e o local de expressão inserida  
 Expressões inseridas podem aparecer somente em determinados locais dentro de expressões literais XML. Os controles de local de expressão que tipos de expressão podem retornar e como `Nothing` é tratado. A tabela a seguir descreve os locais permitidos e tipos de expressões inseridas.  
  
|Local no literal|Tipo de expressão|Tratamento de`Nothing`|  
|---|---|---|  
|Nome do elemento XML|<xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>|Erro|  
|Conteúdo de elemento XML|`Object`ou uma matriz de`Object`|Ignorado|  
|Nome do atributo de elemento XML|<xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>|Erro, a menos que o valor do atributo também é`Nothing`|  
|Valor de atributo do elemento XML|`Object`|Declaração de atributo ignorada|  
|Atributo de elemento XML|<xref:System.Xml.Linq.XAttribute>ou uma coleção de<xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute>|Ignorado|  
|Elemento de raiz do documento XML|<xref:System.Xml.Linq.XElement>ou uma coleção de um <xref:System.Xml.Linq.XElement>objeto e um número arbitrário de <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>objetos</xref:System.Xml.Linq.XComment> e</xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>|Ignorado|  
  
-   Exemplo de uma expressão inserida em um nome de elemento XML:  
  
     [!code-vb[32 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   Exemplo de uma expressão inserida no conteúdo de um elemento XML:  
  
     [!code-vb[33 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   Exemplo de uma expressão inserida em um nome de atributo do elemento XML:  
  
     [!code-vb[VbXMLSamples&#34;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   Exemplo de uma expressão inserida em um valor de atributo do elemento XML:  
  
     [!code-vb[VbXMLSamples&#35;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   Exemplo de uma expressão inserida em um atributo de elemento XML:  
  
     [!code-vb[VbXMLSamples&#36;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   Exemplo de uma expressão inserida em um elemento raiz do documento XML:  
  
     [!code-vb[VbXMLSamples&#37;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 Se você habilitar `Option Strict`, o compilador verifica se o tipo de cada expressão inserida se expande para o tipo solicitado. A única exceção é para o elemento raiz de um documento XML, que é verificado quando o código é executado. Se você compilar sem `Option Strict`, você pode inserir expressões do tipo `Object` e seu tipo é verificado em tempo de execução.  
  
 Em locais onde o conteúdo é opcional, que contêm expressões incorporadas `Nothing` são ignorados. Isso significa que você não precise verificar esse conteúdo de elemento, valores de atributos e elementos de matriz não são `Nothing` antes de usar um literal XML. Necessário valores, como nomes de elementos e atributos, não podem ser `Nothing`.  
  
 Para obter mais informações sobre como usar uma expressão inserida em um determinado tipo de literal, consulte [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Regras de escopo  
 O compilador converte cada XML literal em uma chamada de construtor para o tipo de literal apropriado. O conteúdo literal e expressões incorporadas em um literal XML são passadas como argumentos para o construtor. Isso significa que todos os [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] elementos de programação disponíveis para um literal XML também estão disponíveis para suas expressões inseridas.  
  
 Um literal XML, você pode acessar o namespace XML prefixos declarados com o `Imports` instrução. Você pode declarar um novo prefixo de namespace XML ou um prefixo de namespace XML existente, em um elemento por meio de sombra a `xmlns` atributo. O novo namespace está disponível para os nós filho do elemento, mas não para literais XML em expressões inseridas.  
  
> [!NOTE]
>  Quando você declarar um prefixo de namespace XML usando o `xmlns` atributo namespace, o valor do atributo deve ser uma cadeia de caracteres constante. Nesse sentido, usando o `xmlns` atributo é como usar o `Imports` declaração para declarar um namespace XML. Você não pode usar uma expressão inserida para especificar o valor de namespace XML.  
  
## <a name="see-also"></a>Consulte também  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Visão Geral dos Literais XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
