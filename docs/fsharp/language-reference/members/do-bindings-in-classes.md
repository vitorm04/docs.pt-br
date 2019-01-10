---
title: Associações do em classes
description: Saiba como usar um F# 'do' associação em uma definição de classe, que executa ações quando o objeto é criado ou quando o tipo é usado pela primeira vez.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddf2b5ca458d0950c2e07bf2c37c205877e2173
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613109"
---
# <a name="do-bindings-in-classes"></a>Associações do em classes

Um `do` associação em uma definição de classe executa ações quando o objeto é construído ou, para um estático `do` associação, quando o tipo é usado primeiro.

## <a name="syntax"></a>Sintaxe

```fsharp
[static] do expression
```

## <a name="remarks"></a>Comentários

Um `do` associação é exibida junto com ou após `let` associações, mas antes de definições de membro em uma definição de classe. Embora o `do` palavra-chave é opcional para o `do` associações no nível de módulo, não é opcional para `do` ligações em uma definição de classe.

Para a construção de cada objeto de qualquer determinado tipo, não estáticos `do` associações e não-estático `let` associações são executadas na ordem em que aparecem na definição de classe. Vários `do` associações podem ocorrer em um tipo. O não-estático `let` associações e não-estático `do` associações tornam-se o corpo do construtor primário. O código não-estático `do` seção de associações pode fazer referência a parâmetros do construtor primário e todos os valores ou funções que são definidas na `let` seção de associações.

Não-estático `do` associações podem acessar membros da classe, desde que a classe tem um identificador de autoatendimento que é definido por um `as` palavra-chave na classe de título e, desde que todos os usos desses membros são qualificados com o identificador de autoatendimento para a classe.

Porque `let` associações inicializar os campos privados de uma classe, que é geralmente necessário para garantir que os membros se comportam conforme o esperado, `do` associações geralmente são colocadas depois `let` associações de forma que o código a `do` associação pode Execute com um objeto totalmente inicializado. Se seu código tentar usar um membro antes que a inicialização é concluída, uma InvalidOperationException é gerada.

Estático `do` ligações podem fazer referência a membros estáticos ou campos de fechamento de classe, mas não campos ou membros de instância. Estático `do` associações se tornam parte do inicializador estático para a classe, que é a garantia de serem executados antes que a classe é usada pela primeira vez.

Atributos são ignorados para `do` associações de tipos. Se um atributo é necessário para o código que é executado em um `do` de associação, ela deverá ser aplicada para o construtor primário.

No código a seguir, uma classe tem um estático `do` associação e um não-estático `do` associação. O objeto tem um construtor que tem dois parâmetros, `a` e `b`, e dois campos particulares são definidos na `let` associações para a classe. Duas propriedades também são definidas. Todos eles estão no escopo em não-estático `do` seção de associações, conforme é ilustrado pela linha que imprime todos esses valores.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

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
- [`do` Associações](../functions/do-Bindings.md)