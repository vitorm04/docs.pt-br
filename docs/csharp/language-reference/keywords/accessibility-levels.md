---
title: "Níveis de acessibilidade (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 30220e92e55ac6101cf8fedd8920755cd25978bd
ms.lasthandoff: 03/13/2017

---
# <a name="accessibility-levels-c-reference"></a>Níveis de acessibilidade (Referência de C#)
Use os modificadores de acesso, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md), para especificar um dos seguintes níveis de acessibilidade declarada de membros.  
  
|Acessibilidade declarada|Significado|  
|----------------------------|-------------|  
|`public`|O acesso não é restrito.|  
|`protected`|O acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém.|  
|`internal`|O acesso é limitado ao assembly atual.|  
|`protected` `internal`|O acesso é limitado ao assembly atual ou aos tipos derivados da classe que os contém.|  
|`private`|O acesso é limitado ao tipo recipiente.|  
  
 Apenas um modificador de acesso é permitido para um membro ou tipo, exceto quando você usa a combinação `protected` `internal`.  
  
 Os modificadores de acesso não são permitidos em namespaces. Namespaces não têm nenhuma restrição de acesso.  
  
 Dependendo do contexto no qual ocorre uma declaração de membro, apenas algumas acessibilidades declaradas são permitidas. Se não for especificado nenhum modificador de acesso em uma declaração de membro, uma acessibilidade padrão será usada.  
  
 Os tipos de nível superior, que não estão aninhados em outros tipos, podem ter apenas a acessibilidade `internal` ou `public`. A acessibilidade de padrão para esses tipos é `internal`.  
  
 Tipos aninhados, que são membros de outros tipos, podem ter acessibilidades declaradas conforme indicado na tabela a seguir.  
  
|Membros de|Acessibilidade de membro padrão|Acessibilidade declarada permitida do membro|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Nenhum|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected` `internal`|  
|`interface`|`public`|Nenhum|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 A acessibilidade de um tipo aninhado depende do [domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md), que é determinado pela acessibilidade declarada do membro e pelo domínio da acessibilidade do tipo imediatamente contido. Entretanto, o domínio de acessibilidade de um tipo aninhado não pode exceder o do tipo contido.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [Restrições ao uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)
