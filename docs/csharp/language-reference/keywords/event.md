---
title: event – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: eb1805ed55921497fea88e6b39989c876ef003d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713565"
---
# <a name="event-c-reference"></a>evento (referência C#)

A palavra-chave `event` é usada para declarar um evento em uma classe publicadora.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como declarar e acionar um evento que usa o <xref:System.EventHandler> como o tipo delegado subjacente. Para o exemplo de código completo que <xref:System.EventHandler%601> também mostra como usar o tipo de delegado genérico e como assinar um evento e criar um método manipulador de eventos, consulte [Como publicar eventos que estejam em conformidade com as Diretrizes-Quadro .NET](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

Os eventos são um tipo especial de delegado multicast que só podem ser invocados de dentro da classe ou struct em que eles são declarados (a classe publicadora). Se outras classes ou structs assinarem o evento, seus respectivos métodos de manipulador de eventos serão chamados quando a classe publicadora acionar o evento. Para obter mais informações e exemplos de código, consulte [Eventos](../../programming-guide/events/index.md) e [Delegados](../../programming-guide/delegates/index.md).

Os eventos podem ser marcados como [públicos,](./public.md) [privados,](./private.md) [protegidos,](./protected.md) [internos,](./internal.md) [internos](./protected-internal.md)ou [privados protegidos.](./private-protected.md) Esses modificadores de acesso definem como os usuários da classe podem acessar o evento. Para obter mais informações, consulte [Modificadores de Acesso](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="keywords-and-events"></a>Palavras-chave e eventos

As palavras-chave a seguir aplicam-se a eventos.

|Palavra-chave|Descrição|Para obter mais informações|
|-------------|-----------------|--------------------------|
|[Estático](./static.md)|Torna o evento disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe.|[Classes static e membros de classes static](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[Virtual](./virtual.md)|Permite que classes derivadas substituam o comportamento do evento, usando a palavra-chave [override](./override.md).|[Herança](../../programming-guide/classes-and-structs/inheritance.md)|
|[sealed](./sealed.md)|Especifica que, para classes derivadas, o evento não é mais virtual.||
|[Abstrata](./abstract.md)|O compilador não gerará mais os blocos de acessador de evento `add` e `remove`, portanto, as classes derivadas devem fornecer sua própria implementação.||

Um evento pode ser declarado como um evento estático, usando apalavra-chave [static](./static.md). Isso torna o evento disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe. Para obter mais informações, consulte [Classes Estáticas e Membros de Classe Estática](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

Um evento pode ser marcado como um evento virtual, usando a palavra-chave [virtual](./virtual.md). Isso habilita as classes derivadas a substituírem o comportamento do evento, usando a palavra-chave [override](./override.md). Para obter mais informações, consulte [Herança](../../programming-guide/classes-and-structs/inheritance.md). Um evento que substitui um evento virtual também pode ser [sealed](./sealed.md), o que especifica que ele não é mais virtual para classes derivadas. Por fim, um evento pode ser declarado [abstract](./abstract.md), o que significa que o compilador não gerará os blocos de acessador de evento `add` e `remove`. Portanto, classes derivadas devem fornecer sua própria implementação.

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Palavras-chave do C#](./index.md)
- [adicionar](./add.md)
- [remover](./remove.md)
- [Modificadores](index.md)
- [Como combinar delegados (Delegados Multicast)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
