---
title: Tipos aninhados (Guia de Programação em C#)
ms.date: 07/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab13c68b638062ab89c90dbfc51b51b8d72d3bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types-c-programming-guide"></a>Tipos aninhados (Guia de Programação em C#)
Um tipo definido em uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md) é denominado tipo aninhado. Por exemplo:  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
Independentemente de o tipo externo ser uma classe ou uma estrutura, tipos aninhados tornam-se [privados](../../../csharp/language-reference/keywords/private.md) por padrão; eles são acessíveis somente de seu tipo recipiente. No exemplo anterior, a classe `Nested` é inacessível para tipos externos. 

Você também pode especificar um [modificador de acesso](../../language-reference/keywords/access-modifiers.md) para definir a acessibilidade de um tipo aninhado, da seguinte maneira:

- Aninhados de tipos de um **classe** pode ser [pública](../../../csharp/language-reference/keywords/public.md), [protegido](../../../csharp/language-reference/keywords/protected.md), [interno](../../../csharp/language-reference/keywords/internal.md), [protegidos internos](../../../csharp/language-reference/keywords/protected-internal.md), [privada](../../../csharp/language-reference/keywords/private.md) ou [privado protegido](../../../csharp/language-reference/keywords/private-protected.md). 

   No entanto, definindo um `protected`, `protected internal` ou `private protected` aninhados classe dentro de um [lacrado classe](../../language-reference/keywords/sealed.md) gera um aviso do compilador [CS0628](../../misc/cs0628.md), "novo membro protegido declarado na classe sealed."
  
- Tipos aninhados de um **struct** podem ser [públicos](../../../csharp/language-reference/keywords/public.md), [internos](../../../csharp/language-reference/keywords/internal.md) ou [particulares](../../../csharp/language-reference/keywords/private.md).
  
O exemplo a seguir torna a classe `Nested` pública:
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 O tipo aninhado ou interno pode acessar o tipo recipiente ou externo. Para acessar o tipo recipiente, passe-o como um argumento ao construtor do tipo aninhado. Por exemplo:  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 Um tipo aninhado tem acesso a todos os membros acessíveis ao seu tipo recipiente. Ele pode acessar membros privados e protegidos do tipo recipiente, incluindo quaisquer membros protegidos herdados.  
  
 Na declaração anterior, o nome completo da classe `Nested` é `Container.Nested`. Este é o nome usado para criar uma nova instância da classe aninhada, da seguinte maneira:  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)
