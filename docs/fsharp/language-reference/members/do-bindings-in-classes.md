---
title: Associações do em classes
description: Saiba como usar uma F# Associação ' do ' em uma definição de classe, que executa ações quando o objeto é construído ou quando o tipo é usado pela primeira vez.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627581"
---
# <a name="do-bindings-in-classes"></a>Associações do em classes

Uma `do` associação em uma definição de classe executa ações quando o objeto é construído ou, para uma `do` associação estática, quando o tipo é usado pela primeira vez.

## <a name="syntax"></a>Sintaxe

```fsharp
[static] do expression
```

## <a name="remarks"></a>Comentários

Uma `do` Associação aparece junto com ou após `let` associações, mas antes das definições de membro em uma definição de classe. Embora a `do` palavra-chave seja `do` opcional para associações no nível do módulo, ela não é opcional `do` para associações em uma definição de classe.

Para a construção de todos os objetos de qualquer tipo, associações não estáticas `do` e associações não-estáticas `let` são executadas na ordem em que aparecem na definição de classe. Várias `do` associações podem ocorrer em um tipo. As associações não estáticas `let` e as vinculações não-estáticas `do` se tornam o corpo do construtor primário. O código na seção de associações não `do` estáticas pode referenciar os parâmetros do construtor primário e quaisquer valores ou funções que estejam definidos `let` na seção associações.

As associações não `do` estáticas podem acessar os membros da classe, desde que a classe tenha um autoidentifier definido por uma `as` palavra-chave no título da classe e, desde que todos os usos desses membros sejam qualificados com o autoidentificador da classe.

Como `let` as associações inicializam os campos privados de uma classe, o que geralmente é necessário para garantir que os membros se `do` comportem conforme o esperado `let` , as associações geralmente são colocadas após `do` associações para que o código na associação possa Execute com um objeto totalmente inicializado. Se o seu código tentar usar um membro antes da conclusão da inicialização, um InvalidOperationException será gerado.

As `do` associações estáticas podem referenciar membros estáticos ou campos da classe delimitadora, mas não membros ou campos de instância. As `do` associações estáticas tornam-se parte do inicializador estático para a classe, que tem a garantia de executar antes de a classe ser usada pela primeira vez.

Os atributos são ignorados para `do` associações em tipos. Se um atributo for necessário para o código que é executado em `do` uma associação, ele deve ser aplicado ao Construtor principal.

No código a seguir, uma classe tem uma associação `do` estática e uma associação não estática `do` . O objeto tem um construtor que tem dois parâmetros, `a` `b`e dois `let` campos privados são definidos nas associações para a classe. Duas propriedades também são definidas. Todos eles estão no escopo na seção de associações não estáticas `do` , como é ilustrado pela linha que imprime todos esses valores.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

A saída é a seguinte.

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Consulte também

- [Membros](index.md)
- [Classes](../classes.md)
- [Construtores](constructors.md)
- [`let`Associações em Classes](let-bindings-in-classes.md)
- [`do`Associações](../functions/do-Bindings.md)
