---
title: "Literal de documento XML (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlLiteralDocument"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "literal de documento [Visual Basic]"
  - "literal de documento XML [Visual Basic]"
  - "documentos XML [Visual Basic], criando"
  - "literais XML [Visual Basic], documento"
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Literal de documento XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um literal representando um objeto <xref:System.Xml.Linq.XDocument>.  
  
## Sintaxe  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`encoding`|Opcional.  Usa a declarar qual codificação do documento de texto literal.|  
|`standalone`|Opcional.  Texto literal.  Deve ser "Sim" ou "não".|  
|`piCommentList`|Opcional.  Lista de instruções de processamento de XML e os comentários XML.  Usa o seguinte formato:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Cada `piComment`pode ser uma das seguintes opções:<br /><br /> -   [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Obrigatório.  Elemento raiz do documento.  O formato é uma das seguintes opções:<br /><br /> <ul><li>[Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Expressão do formulário incorporada `<%=``elementExp``%>`.    O `elementExp` retorna um dos seguintes:<br /><br /> <ul><li>Um objeto <xref:System.Xml.Linq.XElement>.</li><li>Uma coleção que contém um <xref:System.Xml.Linq.XElement> objeto e qualquer número de <xref:System.Xml.Linq.XProcessingInstruction> e <xref:System.Xml.Linq.XComment> objetos.</li></ul></li></ul><br /> Para obter mais informações, consulte [Expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XDocument>.  
  
## Comentários  
 Um literal de documento XML é identificado pela declaração XML no início do literal.  Embora cada literal de documento XML deve ter exatamente um elemento XML de raiz, ele pode ter qualquer número de instruções de processamento de XML e os comentários XML.  
  
 Um literal de documento XML não pode aparecer em um elemento XML.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.  Habilita a cópia de conteúdo de um documento XML e a colagem direta em um programa [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte o documento XML literal em chamadas para o <xref:System.Xml.Linq.XDocument.%23ctor%2A> e <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> construtores.  
  
## Exemplo  
 O exemplo a seguir cria um documento XML que tem um elemento que contém outro elemento, uma instrução de processamento, um comentário e uma declaração XML.  
  
 [!CODE [VbXMLSamples#30](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#30)]  
  
## Consulte também  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Xml.Linq.XProcessingInstruction>   
 <xref:System.Xml.Linq.XComment>   
 <xref:System.Xml.Linq.XDocument>   
 [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)   
 [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)