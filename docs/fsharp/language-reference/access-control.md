---
title: Controle de acesso
description: Aprenda a controlar o acesso aos elementos de programação, como tipos, métodos e funções, no F# linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: 8db178b26f3beb6ce95bff84ccad9ac9e8c40ce7
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612797"
---
# <a name="access-control"></a>Controle de acesso

*Controle de acesso* refere-se ao declarar a quais clientes podem usar determinados elementos do programa, como tipos, métodos e funções.

## <a name="basics-of-access-control"></a>Noções básicas de controle de acesso

No F#, os especificadores de controle de acesso `public`, `internal`, e `private` pode ser aplicado a módulos, tipos, métodos, definições de valor, funções, propriedades e campos explícitos.

- `public` indica que a entidade pode ser acessada por todos os chamadores.

- `internal` indica que a entidade pode ser acessada somente do mesmo assembly.

- `private` indica que a entidade pode ser acessada somente de módulo ou tipo de delimitador.

> [!NOTE]
> O especificador de acesso `protected` não é usado no F#, embora seja aceitável se você estiver usando tipos criados em linguagens que dão suporte a `protected` acesso. Portanto, se você substituir um método protegido, o método permanece acessível somente dentro da classe e seus descendentes.

Em geral, o especificador é colocado na frente do nome da entidade, exceto quando um `mutable` ou `inline` especificador for usado, o que aparecer após o especificador de controle de acesso.

Se nenhum especificador de acesso for usado, o padrão é `public`, exceto para `let` associações em um tipo, que são sempre `private` para o tipo.

As assinaturas no F# fornecem outro mecanismo para controlar o acesso ao F# elementos do programa. Assinaturas não são necessárias para controle de acesso. Para saber mais, confira [Assinaturas](signatures.md).

## <a name="rules-for-access-control"></a>Regras para o controle de acesso

Controle de acesso está sujeito às seguintes regras:

- Declarações de herança (ou seja, o uso de `inherit` para especificar uma classe base para uma classe), declarações (isto é, especificando que uma classe implementa uma interface) de interface e abstrair os membros têm sempre a mesma acessibilidade que o tipo delimitador. Portanto, um especificador de controle de acesso não pode ser usado nessas construções.

- Acessibilidade para casos individuais em uma união discriminada é determinada pela acessibilidade da união discriminada em si. Ou seja, um caso específico de união é não menos acessível do que a própria união.

- Acessibilidade campos individuais de um tipo de registro não não determinada pela acessibilidade do registro em si. Ou seja, um rótulo de determinado registro é não menos acessível que o registro em si.

## <a name="example"></a>Exemplo

O código a seguir ilustra o uso dos especificadores de controle de acesso. Existem dois arquivos no projeto, `Module1.fs` e `Module2.fs`. Cada arquivo é implicitamente um módulo. Portanto, há dois módulos, `Module1` e `Module2`. Um tipo particular e um tipo interno são definidos em `Module1`. O tipo particular não pode ser acessado de `Module2`, mas o tipo interno pode.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

O código a seguir testa a acessibilidade dos tipos criados no `Module1.fs`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Assinaturas](signatures.md)