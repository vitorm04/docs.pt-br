---
title: "O tipo &#39;&lt;typename&gt;&#39; n&#227;o est&#225; definido | Microsoft Docs"
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
  - "vbc30002"
  - "bc30002"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30002"
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt;typename&gt;&#39; n&#227;o est&#225; definido
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A instrução faz referência a um tipo que não foi definido.  Você pode definir um tipo em uma instrução de declaração, como `Enum`, `Structure`, `Class`, ou `Interface`.  
  
 **Identificação do erro:**  BC30002  
  
### Para corrigir este erro  
  
-   Certifique\-se de que a definição de tipo e sua referência usam a mesma ortografia.  
  
-   Certifique\-se de que a definição de tipo é acessível para a referência.  Por exemplo, se o tipo é outro módulo e foi declarado `Private`, move a definição de tipo para o módulo de referência ou declará\-lo `Public`.  
  
-   Certifique\-se de que o espaço para nome do tipo não foi redefinido dentro de seu projeto.  Se estiver, use o `Global` palavra\-chave para qualificar totalmente o nome de tipo.  Por exemplo, se um projeto define um namespace chamado `System`, o <xref:System.Object?displayProperty=fullName> tipo não pode ser acessado, a menos que ele seja totalmente qualificado com o `Global` palavra\-chave: `Global.System.Object`.  
  
-   Se o tipo é definido, mas a biblioteca de objetos ou em que é definido de biblioteca de tipos não está registrada no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], clique em  **Add Reference** sobre o  **projeto** menu e, em seguida, selecione a biblioteca de objeto apropriado ou a biblioteca de tipos.  
  
-   Certifique\-se de que o tipo é um assembly que faz parte do destino.Perfil do NET Framework.  Para obter mais informações, consulte [Solução de problemas com erros de direcionamento do .NET Framework](/visual-studio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## Consulte também  
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Gerenciando referências em um projeto](/visual-studio/ide/managing-references-in-a-project)