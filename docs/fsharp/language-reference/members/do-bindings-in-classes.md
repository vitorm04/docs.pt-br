---
title: Associações do em classes (F#)
description: "Saiba como usar uma linguagem F # 'do' associação em uma definição de classe, que executa ações quando o objeto é criado ou quando o tipo é usado pela primeira vez."
ms.date: 05/16/2016
ms.openlocfilehash: 779b33c44b1518135f4c7f270173ec8124fec101
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="do-bindings-in-classes"></a>Associações do em classes

Um `do` associação em uma definição de classe executa ações quando o objeto for construído ou, para um static `do` associação, quando o tipo de primeira será usado.


## <a name="syntax"></a>Sintaxe

```fsharp
[static] do expression
```

## <a name="remarks"></a>Comentários
Um `do` associação aparece junto com ou após `let` associações, mas antes de definições de membro em uma definição de classe. Embora o `do` palavra-chave é opcional para `do` associações no nível de módulo, não é opcional para `do` associações em uma definição de classe.

Para a construção de todos os objetos de qualquer tipo, não estático fornecido `do` associações e não-estático `let` associações são executadas na ordem em que aparecem na definição de classe. Vários `do` associações podem ocorrer em um tipo. O não-estático `let` associações e não-estático `do` associações tornam-se o corpo do construtor primário. O código de não-estático `do` seção associações pode referenciar os parâmetros do construtor primário e todos os valores ou funções que estão definidas no `let` seção associações.

Não-estático `do` associações podem acessar membros da classe, contanto que a classe tenha um identificador de autoatendimento que é definido por um `as` palavra-chave na classe de título e, desde que todos os usos dos membros são qualificados com o identificador de autoatendimento para a classe.

Porque `let` associações inicializar os campos particulares de uma classe, que é geralmente necessário para garantir que os membros se comportam como esperado, `do` associações são geralmente colocadas após `let` associações de forma que o código no `do` pode associação Execute com um objeto completamente inicializado. Se seu código tentar usar um membro antes da inicialização é concluída, um InvalidOperationException é gerado.

Estático `do` associações podem fazer referência a membros estáticos ou campos de circunscrição de classe, mas não membros ou campos de instância. Estático `do` associações se tornam parte do inicializador estático da classe, que é garantido para executar antes que a classe é usada pela primeira vez.

Atributos são ignorados para `do` associações em tipos. Se um atributo é necessário para o código que é executado em um `do` de associação, ela deverá ser aplicada ao construtor primário.

No código a seguir, uma classe tem um estático `do` de associação e não-estático `do` associação. O objeto tem um construtor que tem dois parâmetros, `a` e `b`, e os dois campos particulares são definidos no `let` associações para a classe. Duas propriedades também são definidas. Todos eles estão no escopo em não-estático `do` seção associações, conforme ilustrado pela linha que imprime todos esses valores.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

A saída é a seguinte.

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Consulte também
[Membros](index.md)

[Classes](../classes.md)

[Construtores](constructors.md)

[`let`Associações em Classes](let-bindings-in-classes.md)

[`do` Associações](../functions/do-Bindings.md)
