---
title: "&lt;include&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Marca &lt;include&gt; (XML)"
  - "marca XML include"
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;include&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Refere\-se a outro arquivo que descreve os tipos e membros em seu código\-fonte.  
  
## Sintaxe  
  
```  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### Parâmetros  
 `filename`  
 Obrigatório.  O nome do arquivo que contém a documentação.  O nome do arquivo pode ser qualificado com um caminho.  Coloque `filename` entre aspas duplas \(""\).  
  
 `tagpath`  
 Obrigatório.  O caminho nas marcas `filename` que leva a marca de `name`.  Coloque o caminho entre aspas duplas \(""\).  
  
 `name`  
 Obrigatório.  O especificador de nome na marca que precede os comentários.  `Name`terá um `id`.  
  
 `id`  
 Obrigatório.  A identificação de marca que precede os comentários.  Coloque a identificação de aspas simples \(' '\).  
  
## Comentários  
 Use o `<include>` marca para se referir a comentários em outro arquivo que descrevem os tipos e membros em seu código\-fonte.  Essa é uma alternativa à colocação de comentários da documentação diretamente no seu arquivo de código\-fonte.  
  
 O `<include>` marca usa a recomendação versão 1.0 do W3C XML Path Language \(XPath\).  Mais informações sobre maneiras de personalizar seu `<include>` uso está disponível em http:\/\/www.w3.org\/TR\/xpath.  
  
## Exemplo  
 Este exemplo usa a `<include>` marca para importar comentários de documentação do membro de um arquivo chamado `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 O formato do `commentFile.xml` é o seguinte.  
  
```  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)