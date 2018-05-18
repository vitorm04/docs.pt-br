---
title: Novidades no C# 7.2
description: Uma visão geral dos novos recursos no C# 7.2.
ms.date: 08/16/2017
ms.openlocfilehash: b813bf5b38ef17986b21e928c9c86e583174c7d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-72"></a>Novidades no C# 7.2

O C# 7.2 é outra versão de ponto que adiciona vários recursos úteis.
Um tema desta versão é o trabalho com maior eficiência com tipos de valor, evitando cópias ou alocações desnecessárias. 

Os recursos restantes são pequenos e agradáveis.

O C# 7.2 usa o elemento de configuração de [seleção de versão de linguagem](csharp-7-1.md#language-version-selection) para selecionar a versão de linguagem do compilador.

Os novos recursos de linguagem nesta versão são:

* [Semântica de referência com tipos de valor](#reference-semantics-with-value-types)
  - Uma combinação de aprimoramentos de sintaxe que permitem trabalhar com tipos de valor usando a semântica de referência.
* [Argumentos nomeados que não estejam à direita](#non-trailing-named-arguments)
  - Os argumentos nomeados podem ser seguidos por argumentos posicionais.
* [Sublinhados à esquerda em literais numéricos](#leading-underscores-in-numeric-literals)
  - Agora os literais numéricos podem ter sublinhados à esquerda, antes dos dígitos impressos.
* [Modificador de acesso `private protected`](#private-protected-access-modifier)
  - O modificador de acesso `private protected` permite o acesso a classes derivadas no mesmo assembly.

## <a name="reference-semantics-with-value-types"></a>Semântica de referência com tipos de valores

Os recursos de linguagem introduzidos na 7.2 permitem trabalhar com tipos de valor ao usar semântica de referência. Eles são projetados para melhorar o desempenho, minimizando a cópia de tipos de valor sem incorrer nas alocações de memória associadas ao uso de tipos de referência. Os recursos incluem:

 - O modificador `in` em parâmetros, para especificar que um argumento é passado por referência, mas não modificado pelo método chamado.
 - O modificador `ref readonly` nos retornos de método, para indicar que um método retorna seu valor por referência, mas não permite gravações nesse objeto.
 - A declaração `readonly struct`, para indicar que uma struct é imutável e deve ser passado como um parâmetro `in` para seus métodos de membro.
 - A declaração `ref struct`, para indicar que um tipo de struct acessa a memória gerenciada diretamente e deve sempre ser alocado por pilha.

Você pode ler mais sobre todas essas alterações em [Uso de tipos de valor com a semântica de referência](../reference-semantics-with-value-types.md).

## <a name="non-trailing-named-arguments"></a>Argumentos nomeados que não estejam à direita

Agora as chamadas de método podem usar argumentos nomeados que precedem argumentos posicionais quando esses argumentos nomeados estão nas posições corretas. Para obter mais informações, consulte [Argumentos nomeados e opcionais](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Sublinhados à esquerda em literais numéricos

A implementação de suporte para separadores de dígitos no C# 7.0 não permite que o `_` esteja no primeiro caractere do valor literal. Agora os literais numéricos binários e hexadecimais podem começar com um `_`. 

Por exemplo:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>modificador de acesso _protegido privado_

Por fim, um novo modificador de acesso composto: `private protected` indica que um membro pode ser acessado pela classe que o contém ou por classes derivadas que são declaradas no mesmo assembly. Enquanto que `protected internal` permite o acesso por classes derivadas ou classes que estejam no mesmo assembly, o `private protected` limita o acesso a tipos derivados declarados no mesmo assembly.

Para obter mais informações, consulte [modificadores de acesso](../language-reference/keywords/access-modifiers.md) na referência de linguagem.
