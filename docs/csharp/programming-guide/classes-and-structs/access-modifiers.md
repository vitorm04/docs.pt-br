---
title: Modificadores de acesso – Guia de Programação em C#
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628222"
---
# <a name="access-modifiers-c-programming-guide"></a>Modificadores de acesso (Guia de Programação em C#)

Todos os tipos e tipos de membros têm um nível de acessibilidade. O nível de acessibilidade controla se eles podem ser usados a partir de outro código em sua montagem ou outras assembléias. Use os modificadores de acesso a seguir para especificar a acessibilidade de um tipo ou membro quando você declara-lo:

- [público](../../language-reference/keywords/public.md): O tipo ou membro pode ser acessado por qualquer outro código no mesmo conjunto ou outro conjunto que o faça referência.
- [privado](../../language-reference/keywords/private.md): O tipo ou membro pode ser `class` acessado `struct`apenas por código no mesmo ou .
- [protegido](../../language-reference/keywords/protected.md): O tipo ou membro pode ser `class`acessado apenas `class` por código no `class`mesmo , ou em um que é derivado disso .
- [interno](../../language-reference/keywords/internal.md): O tipo ou membro pode ser acessado por qualquer código no mesmo conjunto, mas não de outro conjunto.
- [interno protegido](../../language-reference/keywords/protected-internal.md): O tipo ou membro pode ser acessado por qualquer código na assembléia em `class` que seja declarado, ou de dentro de um derivado em outra assembléia.
- [privado protegido](../../language-reference/keywords/private-protected.md): O tipo ou membro só pode ser acessado dentro `class` de sua assembléia declarativa, `class`por código no mesmo ou em um tipo derivado disso .

Os exemplos a seguir demonstram como especificar modificadores de acesso em um tipo e membro:

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Nem todos os modificadores de acesso são válidos para todos os tipos ou membros em todos os contextos. Em alguns casos, a acessibilidade de um membro tipo é limitada pela acessibilidade de seu tipo de contêm.

## <a name="class-and-struct-accessibility"></a>Acessibilidade de classe e estrutura  

Classes e estruturas declaradas diretamente dentro de um namespace (em outras palavras, que não estão aninhadas em outras classes ou estruturas) podem ser ou `public` `internal`. `Internal`é o padrão se nenhum modificador de acesso for especificado.  

Membros de estrutura, incluindo classes aninhadas e estruturas, `public` `internal`podem `private`ser declarados, ou . Os membros da classe, incluindo classes aninhadas `protected`e `internal` `private protected`estruturas, `private`podem ser, `public`, `protected internal`, , ou . Membros de classe e estrutura, incluindo classes aninhadas `private` e estruturas, têm acesso por padrão. Os tipos aninhados privados não são acessíveis de fora do tipo que contém.

Classes derivadas não podem ter maior acessibilidade do que seus tipos de base. Você não pode declarar `B` uma classe pública que `A`deriva de uma classe interna. Se permitido, teria o efeito `A` de tornar `protected` `internal` público, `A` porque todos ou membros de são acessíveis a partir da classe derivada.

Você pode habilitar outros conjuntos específicos para `InternalsVisibleToAttribute`acessar seus tipos internos usando o . Para obter mais informações, consulte [Assemblies amigáveis](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Acessibilidade de membros de classe e estrutura  

Os membros de classe (incluindo as classes e os structs aninhados) podem ser declarados com qualquer um dos seis tipos de acesso. Os membros da estrutura não podem `protected` `protected internal`ser `private protected` declarados como , ou porque as estruturas não suportam herança.

Normalmente, a acessibilidade de um membro não é maior do que a acessibilidade do tipo que o contém. No entanto, um `public` membro de uma classe interna pode ser acessível de fora da montagem se o membro implementar métodos de interface ou anular métodos virtuais definidos em uma classe de base pública.

O tipo de campo, propriedade ou evento de qualquer membro deve ser pelo menos tão acessível quanto o próprio membro. Da mesma forma, o tipo de retorno e os tipos de parâmetros de qualquer método, indexador ou delegado devem ser pelo menos tão acessíveis quanto o próprio membro. Por exemplo, você não `public` pode `M` ter um `C` `C` método `public`que retorna uma classe a menos que também seja . Da mesma forma, você `protected` não pode `A` `A` ter uma `private`propriedade do tipo se for declarada como .

As operadoras definidas pelo usuário `public` `static`devem ser sempre declaradas como e . Para obter mais informações, consulte [Sobrecarga de operador](../../language-reference/operators/operator-overloading.md).

Os finalizadores não podem ter modificadores de acessibilidade.

Para definir o nível `class` `struct` de acesso para um ou membro, adicione a palavra-chave apropriada à declaração do membro, conforme mostrado no exemplo a seguir.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Outros tipos

Interfaces declaradas diretamente dentro de `public` `internal` um namespace podem ser ou, assim como `internal` classes e estruturas, interfaces padrão de acesso. Os membros `public` da interface são por padrão porque o propósito de uma interface é permitir que outros tipos acessem uma classe ou estrutura. As declarações dos membros da interface podem incluir qualquer modificador de acesso. Isso é mais útil para métodos estáticos para fornecer implementações comuns necessárias por todos os implementores de uma classe.

Os membros de `public`enumeração são sempre , e nenhum modificador de acesso pode ser aplicado.

Delegados se comportam como classes e structs. Por padrão, `internal` eles têm acesso quando declarados `private` diretamente dentro de um namespace e acessam quando aninhados.

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Classes e structs](./index.md)
- [Interfaces](../interfaces/index.md)
- [Privada](../../language-reference/keywords/private.md)
- [público](../../language-reference/keywords/public.md)
- [Interno](../../language-reference/keywords/internal.md)
- [Protegido](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/builtin-types/struct.md)
- [Interface](../../language-reference/keywords/interface.md)
