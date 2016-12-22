---
title: "N&#237;veis de acessibilidade (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "modificadores de acesso [C#], níveis de acessibilidade"
  - "níveis de acessibilidade"
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# N&#237;veis de acessibilidade (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Use os modificadores de acesso,  [pública](../../../csharp/language-reference/keywords/public.md),  [protegido](../../../csharp/language-reference/keywords/protected.md),  [interno](../../../csharp/language-reference/keywords/internal.md), ou  [particular](../../../csharp/language-reference/keywords/private.md), para especificar um dos seguintes níveis de acessibilidade declarada de membros.  
  
|Acessibilidade declarada|Significado|  
|------------------------------|-----------------|  
|`public`|O acesso não é restrito.|  
|`protected`|O acesso é limitado a classe que contém classes ou tipos derivados da classe que contém.|  
|`internal`|O acesso é limitado ao conjunto atual.|  
|`protected` `internal`|O acesso é limitado ao conjunto atual ou tipos derivados da classe que contém.|  
|`private`|O acesso é limitado para o tipo de recipiente.|  
  
 Modificador de acesso somente uma é permitido para um membro ou tipo, exceto quando você usa o `protected``internal` combinação.  
  
 Modificadores de acessos não são permitidos em namespaces.  Namespaces não têm restrições de acesso.  
  
 Dependendo do contexto no qual ocorre uma declaração de membro, somente algumas acessibilidades declaradas são permitidas.  Se nenhum modificador de acesso é especificado na declaração de membro, uma acessibilidade padrão é usada.  
  
 Tipos de nível superior, que não estão aninhados em outros tipos, só podem ter `internal` ou `public` acessibilidade.  A acessibilidade padrão para esses tipos for `internal`.  
  
 Tipos aninhados, que são membros de outros tipos, podem ter acessibilidade declarada, conforme indicado na tabela a seguir.  
  
|Membros do|Acessibilidade de membro padrão|Acessibilidade declarada permitida dos membros|  
|----------------|-------------------------------------|----------------------------------------------------|  
|`enum`|`public`|Nenhum|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected` `internal`|  
|`interface`|`public`|Nenhum|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 A acessibilidade de um tipo aninhado depende de sua  [o domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md), que é determinado pela acessibilidade declarada do membro e o domínio de acessibilidade do tipo imediatamente contido.  Entretanto, o domínio de acessibilidade de um tipo aninhado não pode exceder o do tipo contido.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [Restrições ao uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)