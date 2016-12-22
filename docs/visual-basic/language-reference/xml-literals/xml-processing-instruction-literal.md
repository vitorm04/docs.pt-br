---
title: "Literal de instru&#231;&#227;o de processamento XML (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlLiteralProcessingInstruction"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "processando literal de instrução [Visual Basic]"
  - "literais XML [Visual Basic], instrução de processamento"
  - "processando literal de instrução XML [Visual Basic]"
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Literal de instru&#231;&#227;o de processamento XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um literal representando um objeto <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## Sintaxe  
  
```  
<?piName [ = piData ] ?>  
```  
  
## Partes  
 `<?`  
 Obrigatório.  Indica o início da instrução de processamento XML literal.  
  
 `piName`  
 Obrigatório.  O nome que indica qual aplicativo os destinos de instrução de processamento.  Não pode começar com "xml" ou "XML".  
  
 `piData`  
 Opcional.  String que indica como o aplicativo alvo de `piName` deve processar o documento XML.  
  
 `?>`  
 Obrigatório.  Indica o final da instrução de processamento.  
  
## Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## Comentários  
 Literais de instrução de processamento XML indicam como os aplicativos devem processar um documento XML.  Quando um aplicativo carrega um documento XML, o aplicativo pode verificar as instruções de processamento de XML para determinar como processar o documento.  O aplicativo interpreta o significado de `piName` e `piData`.  
  
 O documento XML literal usa a sintaxe é semelhante da instrução de processamento de XML.  Para obter mais informações, consulte [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
>  O `piName` elemento não pode começar com as seqüências de caracteres "xml" ou "XML", porque esses identificadores de reserva a especificação XML 1.0.  
  
 Você pode atribuir uma instrução de processamento XML literal a uma variável ou incluí\-lo em um literal de documento XML.  
  
> [!NOTE]
>  Um literal XML pode ocupar várias linhas, sem a necessidade de caracteres de continuação de linha.  Habilita a cópia de conteúdo de um documento XML e a colagem direta em um programa [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte a instrução de processamento XML literal para uma chamada para o <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> construtor.  
  
## Exemplo  
 O exemplo a seguir cria uma instrução de processamento identificando uma folha de estilo para um documento XML.  
  
 [!CODE [VbXMLSamples#28](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#28)]  
  
## Consulte também  
 <xref:System.Xml.Linq.XProcessingInstruction>   
 [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)