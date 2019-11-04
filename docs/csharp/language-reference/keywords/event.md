---
title: event – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: a6a62881f7205891bafe039a42da44eb8f8d03c0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422824"
---
# <a name="event-c-reference"></a>event (Referência de C#)
A palavra-chave `event` é usada para declarar um evento em uma classe publicadora.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar e acionar um evento que usa o <xref:System.EventHandler> como o tipo delegado subjacente. Para obter o exemplo de código completo, que também mostra como usar o tipo delegado <xref:System.EventHandler%601> genérico e como assinar um evento e criar um método de manipulador de eventos, consulte [Como publicar eventos em conformidade com as diretrizes do .NET Framework](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 Os eventos são um tipo especial de delegado multicast que só podem ser invocados de dentro da classe ou struct em que eles são declarados (a classe publicadora). Se outras classes ou structs assinarem o evento, seus respectivos métodos de manipulador de eventos serão chamados quando a classe publicadora acionar o evento. Para obter mais informações e exemplos de código, consulte [Eventos](../../programming-guide/events/index.md) e [Delegados](../../programming-guide/delegates/index.md).  
  
 Os eventos podem ser marcados como [public](./public.md), [private](./private.md), [protected](./protected.md), [internal](./internal.md), [protected internal](./protected-internal.md) ou [private protected](./private-protected.md). Esses modificadores de acesso definem como os usuários da classe podem acessar o evento. Para obter mais informações, consulte [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="keywords-and-events"></a>Palavras-chave e eventos  
 As palavras-chave a seguir aplicam-se a eventos.  
  
|Palavra-chave|Descrição|Para obter mais informações|  
|-------------|-----------------|--------------------------|  
|[static](./static.md)|Torna o evento disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe.|[Classes static e membros de classes static](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](./virtual.md)|Permite que classes derivadas substituam o comportamento do evento, usando a palavra-chave [override](./override.md).|[Herança](../../programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](./sealed.md)|Especifica que, para classes derivadas, o evento não é mais virtual.||  
|[abstract](./abstract.md)|O compilador não gerará mais os blocos de acessador de evento `add` e `remove`, portanto, as classes derivadas devem fornecer sua própria implementação.||  
  
 Um evento pode ser declarado como um evento estático, usando apalavra-chave [static](./static.md). Isso torna o evento disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe. Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Um evento pode ser marcado como um evento virtual, usando a palavra-chave [virtual](./virtual.md). Isso habilita as classes derivadas a substituírem o comportamento do evento, usando a palavra-chave [override](./override.md). Para obter mais informações, consulte [Herança](../../programming-guide/classes-and-structs/inheritance.md). Um evento que substitui um evento virtual também pode ser [sealed](./sealed.md), o que especifica que ele não é mais virtual para classes derivadas. Por fim, um evento pode ser declarado [abstract](./abstract.md), o que significa que o compilador não gerará os blocos de acessador de evento `add` e `remove`. Portanto, classes derivadas devem fornecer sua própria implementação.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](./index.md)
- [add](./add.md)
- [remove](./remove.md)
- [Modificadores](index.md)
- [Como combinar delegados (delegados multicast)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
