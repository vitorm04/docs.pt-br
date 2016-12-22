---
title: "Marcas XML recomendadas para coment&#225;rios da documenta&#231;&#227;o (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlDocComment"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comentários, marcas XML recomendadas"
  - "marcas, XML"
  - "comentários XML, marcas recomendadas [Visual Basic]"
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Marcas XML recomendadas para coment&#225;rios da documenta&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pode processar comentários de documentação em seu código para um arquivo XML.  Você pode usar as ferramentas adicionais para processar o arquivo XML em documentação.  
  
 Comentários XML são permitidos em construções de código, como tipos e membros de tipos.  Para tipos parciais, apenas uma parte do tipo pode ter comentários XM, embora não haja nenhuma restrição em comentar seus membros.  
  
> [!NOTE]
>  Comentários de Documentação não podem ser aplicados a espaços de nome.  O motivo é que um espaço de nomes pode abranger vários conjuntos de módulos \(assemblys\), e não todos os conjuntos de módulos \(assemblys\) têm que ser carregados ao mesmo tempo.  
  
 O compilador processa qualquer marca que é XML válido.  As seguintes marcas fornecem funcionalidades comumente usadas na documentação do usuário.  
  
||||  
|-|-|-|  
|[\<c\>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<código\>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example\>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception\>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include\>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list\>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para\>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param\>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref\>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission\>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks\>](../Topic/%3Cremarks%3E%20\(Visual%20Basic\).md)|[\<returns\>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see\>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso\>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary\>](../Topic/%3Csummary%3E%20\(Visual%20Basic\).md)|  
|[\<typeparam\>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value\>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 \(<sup>1</sup> o compilador verifica a sintaxe.\)  
  
> [!NOTE]
>  Se você quiser que colchetes angulares sejam exibido no texto de um comentário de documentação, use `<` e `>`.  Por exemplo, a sequência de caracteres `"<text in angle brackets>"` aparecerá como `<text in angle` `brackets>`.  
  
## Consulte também  
 [Documentando o código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [Como criar documentação XML](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)