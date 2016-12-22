---
title: "Marcas recomendadas para coment&#225;rios de documenta&#231;&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marcas XML [c#],"
  - "Marcas de documentação XML [c#],"
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Marcas recomendadas para coment&#225;rios de documenta&#231;&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O compilador C\# processa os comentários de documentação no seu código e formatar\-los como XML em um arquivo cujo nome você especifique a opção de linha de comando de **\/doc** .  Para criar documentação final com base no arquivo compilador\-geradas, você pode criar uma ferramenta personalizada, ou usar uma ferramenta como [Castelo de confiança](http://shfb.codeplex.com/).  
  
 As marcas são processadas em construções de código como tipos e membros do tipo.  
  
> [!NOTE]
>  Comentários de documentação não podem ser aplicados a um namespace.  
  
 O compilador processará qualquer marca que é XML válido.  As seguintes marcas fornecem funcionalidades comumente usadas na documentação do usuário.  
  
## Marcas  
  
||||  
|-|-|-|  
|[\<c\>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para\>](../../../csharp/programming-guide/xmldoc/para.md)|[\<see\>](../../../csharp/programming-guide/xmldoc/see.md)\*|  
|[\<código\>](../../../csharp/programming-guide/xmldoc/code.md)|[\<param\>](../../../csharp/programming-guide/xmldoc/param.md)\*|[\<seealso\>](../../../csharp/programming-guide/xmldoc/seealso.md)\*|  
|[\<example\>](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref\>](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<summary\>](../Topic/%3Csummary%3E%20\(C%23%20Programming%20Guide\).md)|  
|[\<exception\>](../../../csharp/programming-guide/xmldoc/exception.md)\*|[\<permission\>](../../../csharp/programming-guide/xmldoc/permission.md)\*|[\<typeparam\>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*|  
|[\<include\>](../../../csharp/programming-guide/xmldoc/include.md)\*|[\<remarks\>](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref\>](../Topic/%3Ctypeparamref%3E%20\(C%23%20Programming%20Guide\).md)|  
|[\<list\>](../../../csharp/programming-guide/xmldoc/list.md)|[\<returns\>](../../../csharp/programming-guide/xmldoc/returns.md)|[\<value\>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 \(\* indica que o compilador verifica a sintaxe.\)  
  
 Se você deseja que os colchetes angulares sejam exibido no texto da documentação, use `<` e `>`, conforme mostrado no exemplo o seguir.  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Comentários de documentação XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)