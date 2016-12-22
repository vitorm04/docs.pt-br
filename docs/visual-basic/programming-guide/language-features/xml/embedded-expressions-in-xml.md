---
title: "Express&#245;es inseridas no XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlEmbeddedExpression"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "expressões inseridas [Visual Basic]"
  - "LINQ to XML [Visual Basic], expressões inseridas"
  - "literais XML [Visual Basic], expressões inseridas"
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#245;es inseridas no XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Expressões incorporadas permitem criar literais XML que contenham expressões são avaliadas no tempo de execução.  A sintaxe de uma expressão incorporada é `<%=``expression``%>`, que é o mesmo, conforme a sintaxe usada em [!INCLUDE[vstecasp](../../../../visual-basic/developing-apps/programming/drives-directories-files/includes/vstecasp_md.md)].  
  
 Por exemplo, você pode criar um elemento XML literal, combinando as expressões incorporadas com conteúdo de texto literal.  
  
 [!CODE [VbXMLSamples#27](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#27)]  
  
 Se `isbnNumber` contém o inteiro 12345 e `modifiedDate` contém a data de 3\/5\/2006, quando esse código é executado, o valor de `book` é:  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## Validação e o local de expressão incorporada  
 Expressões incorporadas podem aparecer apenas em determinados locais dentro de expressões de literais XML.  Os controles de local de expressão que digita a expressão podem retornar e como `Nothing` é tratado.  A tabela a seguir descreve os locais permitidos e os tipos de expressões incorporadas.  
  
||||  
|-|-|-|  
|Local no literal|Tipo de expressão|Tratamento de`Nothing`|  
|Nome do elemento XML|<xref:System.Xml.Linq.XName>|Erro|  
|Conteúdo do elemento XML|`Object`ou matriz de`Object`|Ignorado|  
|Nome do atributo de elemento XML|<xref:System.Xml.Linq.XName>|Erro, a menos que o valor do atributo também é`Nothing`|  
|Valor de atributo do elemento XML|`Object`|Declaração de atributo ignorada|  
|Atributo de elemento XML|<xref:System.Xml.Linq.XAttribute>ou uma coleção de<xref:System.Xml.Linq.XAttribute>|Ignorado|  
|Elemento de raiz do documento XML|<xref:System.Xml.Linq.XElement>ou uma coleção de um <xref:System.Xml.Linq.XElement> objeto e um número arbitrário de <xref:System.Xml.Linq.XProcessingInstruction> e <xref:System.Xml.Linq.XComment> objetos|Ignorado|  
  
-   Exemplo de uma expressão incorporada em um nome de elemento XML:  
  
     [!CODE [VbXMLSamples#32](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#32)]  
  
-   Exemplo de uma expressão incorporada no conteúdo de um elemento XML:  
  
     [!CODE [VbXMLSamples#33](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#33)]  
  
-   Exemplo de uma expressão incorporada em um nome de atributo do elemento XML:  
  
     [!CODE [VbXMLSamples#34](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#34)]  
  
-   Exemplo de uma expressão incorporada em um valor de atributo do elemento XML:  
  
     [!CODE [VbXMLSamples#35](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#35)]  
  
-   Exemplo de uma expressão incorporada em um atributo de elemento XML:  
  
     [!CODE [VbXMLSamples#36](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#36)]  
  
-   Exemplo de uma expressão incorporada em um elemento de raiz do documento XML:  
  
     [!CODE [VbXMLSamples#37](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#37)]  
  
 Se você habilitar `Option Strict`, o compilador verifica que o tipo de cada expressão incorporada amplia para o tipo necessário.  A única exceção é para o elemento raiz de um documento XML, que é verificado quando o código é executado.  Se você compilar sem `Option Strict`, você pode incorporar expressões do tipo `Object` e seu tipo é verificado em tempo de execução.  
  
 Em locais onde o conteúdo é opcional, expressões incorporadas que contêm `Nothing` são ignoradas.  Isso significa que você não precisará verificar o conteúdo de elemento, valores de atributos e elementos de matriz não são `Nothing` antes de usar um literal XML.  Necessário valores, como, por exemplo, nomes de elemento e atributo, não podem ser `Nothing`.  
  
 Para obter mais informações sobre como usar uma expressão incorporada em um determinado tipo de literal, consulte [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## Regras de escopo  
 O compilador converte cada literal XML em uma chamada de construtor para o tipo apropriado de literal.  O conteúdo literal e expressões incorporadas em um literal XML são passadas como argumentos para o construtor.  Isso significa que todos os [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] elementos de programação disponíveis para um literal XML também estão disponíveis para seus expressões incorporadas.  
  
 Dentro de um literal XML, você pode acessar o namespace XML prefixos declarados com o `Imports` instrução.  Você pode declarar um novo prefixo de namespace XML ou sombrear um prefixo de namespace XML existente, em um elemento usando o `xmlns` atributo.  O novo namespace está disponível a nós filho do elemento, mas não literais XML em expressões incorporadas.  
  
> [!NOTE]
>  Quando você declara um prefixo de namespace XML usando o `xmlns` atributo namespace, o valor do atributo deve ser uma seqüência de caracteres constante.  Em relação a isso, usando o `xmlns` atributo é como usar o `Imports` a instrução para declarar um espaço para nome XML.  Você não pode usar uma expressão incorporada para especificar o valor de espaço para nome XML.  
  
## Consulte também  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Instrução Imports \(tipo e namespace .NET\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Visão geral dos literais XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)