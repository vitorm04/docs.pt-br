---
title: "Operador GetXmlNamespace (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.GetXmlNamespace"
  - "GetXmlNamespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Palavra-chave GetXmlNamespace"
  - "Operador GetXmlNamespace"
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador GetXmlNamespace (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Obtém o <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao que o prefixo de namespace XML especificado.  
  
## Sintaxe  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## Partes  
 `xmlNamespacePrefix`  
 Opcional.  A seqüência de caracteres que identifica o prefixo de namespace XML.  Se for fornecido, essa seqüência de caracteres deve ser um identificador XML válido.  Para obter mais informações, consulte [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  Se nenhum prefixo for especificado, o namespace padrão é retornado.  Se nenhum espaço para nome padrão é especificado, o espaço para nome vazio é retornado.  
  
## Valor de retorno  
 O <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML.  
  
## Comentários  
 O `GetXmlNamespace` operador obtém o <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML `xmlNamespacePrefix`.  
  
 Você pode usar os prefixos de namespace XML diretamente no literais XML e propriedades de eixo XML.  Entretanto, você deve usar o `GetXmlNamespace` operador para converter um prefixo de namespace para um <xref:System.Xml.Linq.XNamespace> de objeto antes que você pode usá\-lo em seu código.  Você pode acrescentar um nome de elemento não qualificado para um <xref:System.Xml.Linq.XNamespace> objeto para obter um totalmente qualificado <xref:System.Xml.Linq.XName> object, que muitos [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] métodos requerem.  
  
## Exemplo  
 O exemplo a seguir importa `ns` como um prefixo de namespace XML.  Em seguida, usa o prefixo do namespace para criar um XML literal e acessar o primeiro nó filho que possui o nome qualificado `ns:phone`.  Ele passará o nó filho como o `ShowName` sub\-rotina, que constrói um nome qualificado usando o `GetXmlNamespace` operador.  O `ShowName` sub\-rotina, em seguida, passa o nome qualificado para o <xref:System.Xml.Linq.XNode.Ancestors%2A> método para obter o pai `ns:contact` nó.  
  
 [!CODE [VbXMLSamples#38](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#38)]  
  
 Quando você chama `TestGetXmlNamespace.RunSample()`, ele exibe uma caixa de mensagem que contém o seguinte texto:  
  
 `Name: Patrick Hines`  
  
## Consulte também  
 [Instrução Imports \(namespace XML\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Acessando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)