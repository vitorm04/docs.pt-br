---
title: Controle de acesso (F#)
description: 'Aprenda a controlar o acesso aos elementos de programação, como tipos, métodos e as funções, em F # linguagem de programação.'
ms.date: 05/16/2016
ms.openlocfilehash: 0a5cc1faa1aef343aaca0abb0c42a0dd9a52fcbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566516"
---
# <a name="access-control"></a>Controle de acesso

*Controle de acesso* refere-se ao declarando que os clientes podem usar determinados elementos do programa, como tipos, métodos e funções.


## <a name="basics-of-access-control"></a>Noções básicas de controle de acesso
Em F #, o acesso controle especificadores `public`, `internal`, e `private` pode ser aplicado a módulos, tipos, métodos, definições de valores, funções, propriedades e campos explícitos.


- `public` indica que a entidade pode ser acessada por todos os chamadores.

- `internal` indica que a entidade pode ser acessada somente do mesmo assembly.

- `private` Indica se a entidade pode ser acessada apenas no delimitador tipo ou módulo.


>[!NOTE] 
O especificador de acesso `protected` não é usada em F #, embora seja aceitável se você estiver usando tipos criados em idiomas que dão suporte a `protected` acesso. Portanto, se você substituir um método protegido, o método permanece acessível somente dentro da classe e seus descendentes.

Em geral, o especificador é colocado na frente do nome da entidade, exceto quando uma `mutable` ou `inline` especificador for usado, o que aparecer após o especificador de controle de acesso.

Se nenhum especificador de acesso for usado, o padrão é `public`, exceto para `let` associações em um tipo, que são sempre `private` para o tipo.

Assinaturas em F # fornecem outro mecanismo para controlar o acesso aos elementos do programa F #. As assinaturas não são necessárias para controle de acesso. Para saber mais, confira [Assinaturas](signatures.md).


## <a name="rules-for-access-control"></a>Regras de controle de acesso
Controle de acesso está sujeito às seguintes regras:


- Declarações de herança (ou seja, o uso de `inherit` para especificar uma classe base para uma classe), interface declarações (isto é, especificando uma classe implementa uma interface) e abstrato membros sempre têm a mesma acessibilidade que o tipo de delimitador. Portanto, um especificador de controle de acesso não pode ser usado em dessas construções.

- Casos individuais em uma união discriminada não podem ter seus próprios modificadores de controle de acesso separados do tipo de união.

- Campos individuais de um tipo de registro não podem ter seus próprios modificadores de controle de acesso separados do tipo de registro.


## <a name="example"></a>Exemplo
O código a seguir ilustra o uso de especificadores de controle de acesso. Há dois arquivos no projeto, `Module1.fs` e `Module2.fs`. Cada arquivo é implicitamente um módulo. Portanto, há dois módulos, `Module1` e `Module2`. Um tipo particular e um tipo interno são definidos no `Module1`. O tipo particular não pode ser acessado de `Module2`, mas o tipo interno.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
O código a seguir testa a acessibilidade dos tipos criados no `Module1.fs`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Assinaturas](signatures.md)
