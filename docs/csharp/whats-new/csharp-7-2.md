---
title: Novidades no C# 7.2
description: Uma visão geral dos novos recursos no C# 7.2.
ms.date: 08/16/2017
ms.openlocfilehash: 7ee6d06750f82c9529beaed3cc665f876af08888
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148169"
---
# <a name="whats-new-in-c-72"></a>Novidades no C# 7.2

O C# 7.2 é outra versão de ponto que adiciona vários recursos úteis.
Um tema desta versão é o trabalho com maior eficiência com tipos de valor, evitando cópias ou alocações desnecessárias. 

Os recursos restantes são pequenos e agradáveis.

O C# 7.2 usa o elemento de configuração de [seleção de versão de linguagem](../language-reference/configure-language-version.md) para selecionar a versão de linguagem do compilador.

Os novos recursos de linguagem nesta versão são:

* [Técnicas para escrever código eficiente seguro](#safe-efficient-code-enhancements)
  - Uma combinação de aprimoramentos de sintaxe que permitem trabalhar com tipos de valor usando a semântica de referência.
* [Argumentos nomeados que não estejam à direita](#non-trailing-named-arguments)
  - Os argumentos nomeados podem ser seguidos por argumentos posicionais.
* [Sublinhados à esquerda em literais numéricos](#leading-underscores-in-numeric-literals)
  - Agora os literais numéricos podem ter sublinhados à esquerda, antes dos dígitos impressos.
* [Modificador de acesso `private protected`](#private-protected-access-modifier)
  - O modificador de acesso `private protected` permite o acesso a classes derivadas no mesmo assembly.
* [Expressões `ref` condicionais](#conditional-ref-expressions)
  - O resultado de uma expressão condicional (`?:`) agora já pode ser uma referência.

## <a name="safe-efficient-code-enhancements"></a>Aprimoramentos de código eficiente seguro

Os recursos de linguagem introduzidos na 7.2 permitem trabalhar com tipos de valor ao usar semântica de referência. Eles são projetados para melhorar o desempenho, minimizando a cópia de tipos de valor sem incorrer nas alocações de memória associadas ao uso de tipos de referência. Os recursos incluem:

 - O modificador `in` em parâmetros, para especificar que um argumento é passado por referência, mas não modificado pelo método chamado. Adicionar o modificador `in` a um argumento é uma [alteração compatível com a origem](version-update-considerations.md#source-compatible-changes).
 - O modificador `ref readonly` nos retornos de método, para indicar que um método retorna seu valor por referência, mas não permite gravações nesse objeto. Adicionar o modificador `ref readonly` é uma [alteração compatível com a origem](version-update-considerations.md#source-compatible-changes) se o retorno é atribuído a um valor. Adicionar o modificador `readonly` a uma instrução de retorno `ref` existente é uma [alteração incompatível](version-update-considerations.md#incompatible-changes). Ela requer que os chamadores atualizem a declaração de `ref` variáveis locais para incluir o modificador `readonly`.
 - A declaração `readonly struct`, para indicar que uma struct é imutável e deve ser passado como um parâmetro `in` para seus métodos de membro. Adicionar o modificador `readonly` a uma declaração struct existente é uma [alteração compatível com binário](version-update-considerations.md#binary-compatible-changes).
 - A declaração `ref struct`, para indicar que um tipo de struct acessa a memória gerenciada diretamente e deve sempre ser alocado por pilha. Adicionar o modificador `ref` a uma declaração `struct` existente é uma [alteração incompatível](version-update-considerations.md#incompatible-changes). Um `ref struct` não pode ser um membro de uma classe ou usado em outros locais em que ele pode ser alocado no heap.

Você pode ler mais sobre todas essas alterações em [Escrever código eficiente seguro](../write-safe-efficient-code.md).

## <a name="non-trailing-named-arguments"></a>Argumentos nomeados que não estejam à direita

Agora as chamadas de método podem usar argumentos nomeados que precedem argumentos posicionais quando esses argumentos nomeados estão nas posições corretas. Para obter mais informações, consulte [Argumentos nomeados e opcionais](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Sublinhados à esquerda em literais numéricos

A implementação de suporte para separadores de dígitos no C# 7.0 não permite que o `_` esteja no primeiro caractere do valor literal. Agora os literais numéricos binários e hexadecimais podem começar com um `_`. 

Por exemplo:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>modificador de acesso _protegido privado_

Um novo modificador de acesso composto: `private protected` indica que um membro pode ser acessado pela classe que o contém ou por classes derivadas que são declaradas no mesmo assembly. Enquanto que `protected internal` permite o acesso por classes derivadas ou classes que estejam no mesmo assembly, o `private protected` limita o acesso a tipos derivados declarados no mesmo assembly.

Para obter mais informações, consulte [modificadores de acesso](../language-reference/keywords/access-modifiers.md) na referência de linguagem.

## <a name="conditional-ref-expressions"></a>Expressões `ref` condicionais

Por fim, a expressão condicional pode produzir um resultado ref em vez de um resultado de valor. Por exemplo, você gravaria o seguinte para recuperar uma referência ao primeiro elemento em uma de duas matrizes:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

A variável `r` é uma referência ao primeiro valor em `arr` ou `otherArr`.

Para saber mais, confira [Operador condicional (?:)](../language-reference/operators/conditional-operator.md) na referência da linguagem.
