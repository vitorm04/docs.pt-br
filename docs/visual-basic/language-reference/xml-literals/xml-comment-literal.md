---
title: "Literal de coment&#225;rio XML (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlLiteralComment"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "literal de comentário [Visual Basic]"
  - "literal de comentário XML [Visual Basic]"
  - "comentários XML, adicionando [Visual Basic]"
  - "literais XML [Visual Basic], comment"
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Literal de coment&#225;rio XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um literal representando um objeto <xref:System.Xml.Linq.XComment>.  
  
## Sintaxe  
  
```  
<!-- content -->  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`<!--`|Obrigatório.  Indica o início do comentário XML.|  
|`content`|Obrigatório.  Texto a ser exibido no comentário XML.  Não pode conter uma série de dois hifens \(\-\) ou terminar com um hífen adjacente à marca de fechamento.|  
|`-->`|Obrigatório.  Indica o fim do comentário XML.|  
  
## Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XComment>.  
  
## Comentários  
 Literais de comentário XML não contêm o conteúdo do documento; eles contêm informações sobre o documento.  A seção do comentário XML termina com a sequência "\-\-\> ".  Isso implica nos seguintes pontos\>  
  
-   Você não pode usar uma expressão incorporada em um literal de comentário XML porque os delimitadores de expressão incorporados são conteúdo válido de comentário XML .  
  
-   Seções de comentário XML não podem ser aninhadas, porque `content` não pode conter o valor "\-\-\>".  
  
 Você pode atribuir um comentário XML literal a uma variável, ou você pode incluí\-lo em um literal de elemento XML.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.  Essa ferramenta habilita a cópia de conteúdo de um documento XML e a colagem direta em um programa [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converte o literal de comentário XML para uma chamada ao construtor <xref:System.Xml.Linq.XComment.%23ctor%2A>.  
  
## Exemplo  
 O exemplo a seguir cria um comentário XML que contém o texto "Isto é um comentário".  
  
 [!CODE [VbXMLSamples#9](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#9)]  
  
## Consulte também  
 <xref:System.Xml.Linq.XComment>   
 [Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)