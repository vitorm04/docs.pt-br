---
title: "&lt;permission&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;permission&gt; (XML)"
  - "marca XML de permissão"
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;permission&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica uma permissão necessária para o membro.  
  
## Sintaxe  
  
```  
<permission cref="member">description</permission>  
```  
  
#### Parâmetros  
 `member`  
 Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual.  O compilador verifica se o elemento de código fornecido existe e converte `member` para o nome canônico de elemento na saída XML.  Coloque `member` entre aspas \(" "\).  
  
 `description`  
 Uma descrição do acesso ao membro.  
  
## Comentários  
 Use o marcador `<permission>` para documentar o acesso de um membro.  Use a classe <xref:System.Security.PermissionSet> para especificar o acesso a um membro.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a marca `<permission>` para descrever que <xref:System.Security.Permissions.FileIOPermission> é necessário pelo método `ReadFile`.  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)