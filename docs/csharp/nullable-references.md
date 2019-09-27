---
title: Tipos de referência anuláveis
description: Este artigo fornece uma visão geral dos tipos de referência que permitem valor nulo, adicionados no C# 8. Você aprenderá como o recurso fornece segurança com relação a exceções de referência nula para projetos novos e existentes.
ms.date: 02/19/2019
ms.openlocfilehash: 05a8e14a7c51df685b3ffdf16aab997da0a8036f
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332368"
---
# <a name="nullable-reference-types"></a>Tipos de referência anuláveis

O C# 8.0 apresenta **tipos de referência que permitem valor nulo** e **tipos de referência que não permitem valor nulo** que permitem que você crie importantes instruções sobre as propriedades para variáveis de tipo de referência:

- **Uma referência não deve ser nula**. Quando as variáveis não devem ser nulas, o compilador impõe regras que garantem que seja seguro desreferenciar essas variáveis sem verificar primeiro que ela não está nula:
  - A variável deve ser inicializada para um valor não nulo.
  - A variável nunca pode receber o valor `null`.
- **Uma referência pode ser nula**. Quando variáveis puderem ser nulas, o compilador imporá diferentes regras para garantir que você verificou corretamente se há uma referência nula:
  - a variável só poderá ser desreferenciada quando o compilador puder garantir que o valor não é nulo.
  - Essas variáveis podem ser inicializadas com o valor `null` padrão e receber o valor `null` em outro código.

Esse novo recurso oferece benefícios significativos com relação à manipulação de variáveis de referência em versões anteriores do C#, em que a intenção do design não poderia ser determinada na declaração da variável. O compilador não forneceu segurança com relação a exceções de referência nula para tipos de referência:

- **Uma referência pode ser nula**. Nenhum aviso é emitido quando um tipo de referência é inicializado para nulo ou atribuído posteriormente a nulo.
- **Uma referência é considerada não nula**. O compilador não emite nenhum aviso quando os tipos de referência são desreferenciados. (Com referências que permitem valor nulo, o compilador emite avisos sempre que você desreferencia uma variável que pode ser nula).

Com a adição de tipos de referência que permitem valor nulo, é possível declarar sua intenção mais claramente. O valor `null` é a maneira correta de representar que uma variável não se refere a um valor. Não use esse recurso para remover todos os valores `null` do seu código. Em vez disso, você deve declarar sua intenção par ao compilador e para outros desenvolvedores que leem seu código. Ao declarar sua intenção, o compilador informa quando você escreve um código inconsistente com essa intenção.

Um **tipo de referência que permite valor nulo** é indicado usando a mesma sintaxe que [tipos de valor que permitem valor nulo](programming-guide/nullable-types/index.md): um `?` é acrescentado ao tipo da variável. Por exemplo, a seguinte declaração de variável representa uma variável de cadeia de caracteres que permite valor nulo, `name`:

```csharp
string? name;
```

Qualquer variável em que o `?` não é acrescentado ao nome do tipo é um **tipo de referência que não permite valor nulo**. Isso inclui todas as variáveis de tipo de referência no código existente quando você habilitou esse recurso.

O compilador usa uma análise estática para determinar se uma referência que permite valor nulo é conhecida como não nula. O compilador informa se você desreferencia uma referência quer permite valor nulo quando ela pode ser nula. Você pode substituir esse comportamento usando o `!` **operador NULL-tolerante** seguindo um nome de variável. Por exemplo, se você sabe que a variável `name` não é nula, mas o compilador emite um aviso, é possível escrever o seguinte código para substituir a análise do compilador:

```csharp
name!.Length;
```

é possível ler detalhes sobre esse operador na proposta de especificação de [tipos de referência que permitem valor nulo do rascunho](../../_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) no GitHub.

## <a name="nullability-of-types"></a>Possibilidade de nulidade de tipos

Qualquer tipo de referência pode ter uma das quatro *nulidades*, que descreve quando os avisos são gerados:

- *Não anulável*: Null não pode ser atribuído a variáveis desse tipo. As variáveis desse tipo não precisam ser verificadas quanto à nulidade antes de desreferenciar.
- *Anulável*: Null pode ser atribuído a variáveis desse tipo. Desreferenciar variáveis desse tipo sem verificar primeiro se há `null` gera um aviso.
- *Alheia*: Esse é o estado pré-C# 8. As variáveis desse tipo podem ser desreferenciadas ou atribuídas sem avisos.
- *Desconhecido*: Esse é geralmente para parâmetros de tipo em que restrições não informam o compilador de que o tipo deve ser *anulável* ou *não anulável*.

A nulidade de um tipo em uma declaração de variável é controlada pelo *contexto que permite valor nulo* no qual a variável é declarada.

## <a name="nullable-contexts"></a>Contextos que permitem valor nulo

Contextos que permitem valor nulo habilitam o controle refinado para a maneira como o compilador interpreta variáveis de tipo de referência. O **contexto de anotação que permite valor nulo** de qualquer linha de origem determinada é `enabled` ou `disabled`. Você pode pensar no compilador pré-C# 8 como compilando todo seu código em um contexto que permite valor nulo `disabled`: Qualquer tipo de referência pode ser nulo. O **contexto de avisos anulável** pode ser definido `enabled` como `disabled`ou. O contexto de avisos que permite valor nulo especifica os avisos gerados pelo compilador usando sua análise de fluxo.

O contexto de anotação anulável e o contexto de aviso anulável podem ser definidos para um `Nullable` projeto usando o elemento em seu arquivo *. csproj* . Esse elemento configura como o compilador interpreta a nulidade de tipos e quais avisos são gerados. As configurações válidas são:

- `enable`: O contexto de anotação que permite valor nulo está **habilitado**. O contexto de aviso que permite valor nulo está **habilitado**.
  - Variáveis de um tipo de referência, `string` por exemplo, não permitem valor nulo.  Todos os avisos de nulidade estão habilitados.
- `warnings`: O contexto de anotação que permite valor nulo está **desabilitado**. O contexto de aviso que permite valor nulo está **habilitado**.
  - As variáveis de um tipo de referência são óbvias. Todos os avisos de nulidade estão habilitados.
- `annotations`: O contexto de anotação que permite valor nulo está **habilitado**. O contexto de aviso que permite valor nulo está **desabilitado**.
  - As variáveis de um tipo de referência são óbvias. Todos os avisos de nulidade estão habilitados.
- `disable`: O contexto de anotação que permite valor nulo está **desabilitado**. O contexto de aviso que permite valor nulo está **desabilitado**.
  - As variáveis de um tipo de referência são alheias, como as versões anteriores do C#. Todos os avisos de nulidade estão desabilitados.

Também é possível usar diretivas para definir esses mesmos contextos em qualquer lugar no seu projeto:

- `#nullable enable`: define o contexto de anotação que permite valor nulo e o contexto de aviso que permite valor nulo como **habilitado**.
- `#nullable disable`: define o contexto de anotação que permite valor nulo e o contexto de aviso que permite valor nulo como **desabilitado**.
- `#nullable restore`: restaura o contexto de anotação que permite valor nulo e o contexto de aviso que permite valor nulo para as configurações do projeto.
- `#nullable disable warnings`: definir o contexto de aviso que permite valor nulo como **desabilitado**.
- `#nullable enable warnings`: definir o contexto de aviso que permite valor nulo como **habilitado**.
- `#nullable restore warnings`: restaura o contexto de aviso que permite valor nulo para as configurações do projeto.
- `#nullable disable annotations`: Defina o contexto de anotação anulável como **desabilitado**.
- `#nullable enable annotations`: Defina o contexto de anotação anulável como **habilitado**.
- `#nullable restore annotations`: Restaura o contexto de aviso de anotação para as configurações do projeto.

Os contextos padrão de aviso e de anotação que permitem valor nulo são `disabled`. Essa decisão significa que seu código existente compila sem alterações e sem gerar nenhum aviso novo.

## <a name="nullable-annotation-context"></a>Contexto de anotação que permite valor nulo

O compilador usa as seguintes regras em um contexto de anotação que permite valor nulo desabilitado:

- Não é possível declarar referências que permitem valor nulo em um contexto desabilitado.
- Todas as variáveis de referência podem ser atribuídas a nulo.
- Nenhum aviso é gerado quando uma variável de um tipo de referência é desreferenciado.
- O operador tolerante a nulo pode não ser usado em um contexto desabilitado.

O comportamento é o mesmo que o das versões anteriores de C#.

O compilador usa as seguintes regras em um contexto de anotação que permite valor nulo habilitado:

- Qualquer variável de um tipo de referência é uma **referência que não permite valor nulo**.
- Qualquer referência que não permite valor nulo pode ser desreferenciada com segurança.
- Qualquer tipo de referência que permite valor nulo (indicado pelo `?` após o tipo na declaração de variável) pode ser nulo. A análise estática determina se o valor é conhecido como não nulo quando ele é desreferenciado. Caso contrário, o compilador avisa.
- É possível usar o operador tolerante a nulo para declarar que uma referência que permite valor nulo não é nula.

Em um contexto de anotação que permite valor nulo habilitado, o caractere `?` acrescentado a um tipo de referência declara um **tipo de referência que permite valor nulo**. `!` O **operador NULL-tolerante** pode ser anexado a uma expressão para declarar que a expressão não é nula.

## <a name="nullable-warning-context"></a>Contexto de aviso que permite valor nulo

O contexto de aviso que permite valor nulo é diferente do contexto de anotação que permite valor nulo. Os avisos podem ser habilitados mesmo quando as novas anotações estão desabilitadas. O compilador usa a análise de fluxo estática para determinar o **estado nulo** de qualquer referência. O estado nulo é **não nulo** ou **talvez nulo** quando o *contexto de aviso que permite valor nulo* não está **desabilitado**. Se você desreferenciar uma referência quando o compilador tiver determinado que ela é **talvez nula**, o compilador avisará. O estado de uma referência é **talvez nulo**, a menos que o compilador possa determinar uma das duas condições:

1. A variável foi atribuída definitivamente a um valor não nulo.
1. A variável ou expressão foi marcada novamente como nula antes de desreferenciá-la.

O compilador gera avisos sempre que você desreferenciar uma variável ou expressão em um estado **talvez NULL** quando o contexto de `enabled`aviso anulável for. Além disso, os avisos são gerados quando uma variável ou expressão **talvez nula** é atribuída a um tipo de referência que não permite valor nulo quando o contexto de anotação que permite valor nulo é `enabled`.

## <a name="learn-more"></a>Saiba mais

- [Especificação de referência que permite valor nulo de rascunho](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Introdução ao tutorial de referências que permitem valor nulo](tutorials/nullable-reference-types.md)
- [Migrar uma base de código para referências que permitem valor nulo](tutorials/upgrade-to-nullable-references.md)
