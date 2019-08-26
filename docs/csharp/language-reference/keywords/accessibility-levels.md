---
title: Níveis de acessibilidade – Referência de C#
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 2d6605a305e5003e19f4fe1dd260746302691215
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602393"
---
# <a name="accessibility-levels-c-reference"></a>Níveis de acessibilidade (Referência de C#)

Use os modificadores de acesso, `public`, `protected`, `internal` ou `private`, para especificar um dos níveis de acessibilidade declarada a seguir para membros.  
  
|Acessibilidade declarada|Significado|  
|----------------------------|-------------|  
|[`public`](public.md)|O acesso não é restrito.|  
|[`protected`](protected.md)|O acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém.|  
|[`internal`](internal.md)|O acesso é limitado ao assembly atual.|  
|[`protected internal`](protected-internal.md)|O acesso é limitado ao assembly atual ou aos tipos derivados da classe que os contém.|  
|[`private`](private.md)|O acesso é limitado ao tipo recipiente.|  
|[`private protected`](private-protected.md)|O acesso é limitado à classe que o contém ou a tipos derivados da classe que o contém no assembly atual. Disponível desde o C# 7.2. |  
  
 Apenas um modificador de acesso é permitido para um membro ou tipo, exceto quando você usa as combinações `protected internal` e `private protected`.  
  
 Os modificadores de acesso não são permitidos em namespaces. Namespaces não têm nenhuma restrição de acesso.  
  
 Dependendo do contexto no qual ocorre uma declaração de membro, apenas algumas acessibilidades declaradas são permitidas. Se não for especificado nenhum modificador de acesso em uma declaração de membro, uma acessibilidade padrão será usada.  
  
 Os tipos de nível superior, que não estão aninhados em outros tipos, podem ter apenas a acessibilidade `internal` ou `public`. A acessibilidade de padrão para esses tipos é `internal`.  
  
 Tipos aninhados, que são membros de outros tipos, podem ter acessibilidades declaradas conforme indicado na tabela a seguir.  
  
|Membros de|Acessibilidade de membro padrão|Acessibilidade declarada permitida do membro|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Nenhum|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Nenhum|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 A acessibilidade de um tipo aninhado depende do [domínio de acessibilidade](./accessibility-domain.md), que é determinado pela acessibilidade declarada do membro e pelo domínio da acessibilidade do tipo imediatamente contido. Entretanto, o domínio de acessibilidade de um tipo aninhado não pode exceder o do tipo contido.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](./index.md)
- [Modificadores de acesso](./access-modifiers.md)
- [Domínio de acessibilidade](./accessibility-domain.md)
- [Restrições ao uso de níveis de acessibilidade](./restrictions-on-using-accessibility-levels.md)
- [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
