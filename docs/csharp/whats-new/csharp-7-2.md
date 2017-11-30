---
title: "O que há de novo no c# 7.2"
description: "Uma visão geral dos novos recursos no c# 7.2."
keywords: Design de linguagem c#, 7.2, Visual Studio de 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: a580a4a3a0a49e97ea8fb96699d1d978a9bc0a64
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="whats-new-in-c-72"></a>O que há de novo no c# 7.2

7.2 c# é outra versão do ponto que adiciona um número de recursos úteis.
Um tema para esta versão está trabalhando com mais eficiência com tipos de valor, evitando cópias desnecessárias ou alocações. 

Os recursos restantes são pequenos, ótimo ter recursos.

7.2 c# usa o [seleção de versão de idioma](csharp-7-1.md#language-version-selection) elemento de configuração para selecionar a versão de idioma do compilador.

Os novos recursos de idioma nesta versão são:

* [Semântica de referência com tipos de valor](#reference-semantics-with-value-types)
  - Uma combinação de aprimoramentos de sintaxe que permitem trabalhar com tipos de valor usando a semântica de referência.
* [Argumentos nomeada à direita não](#non-trailing-named-arguments)
  - Argumentos nomeados podem ser seguidos por argumentos posicionais.
* [Sublinhados em literais numéricos](#leading-underscores-in-numeric-literals)
  - Literais numéricos agora podem ter sublinhados antes dos dígitos impressos.
* [`private protected`modificador de acesso](#private-protected)
  - O `private protected` modificador de acesso permite o acesso para classes derivadas no mesmo assembly.

## <a name="reference-semantics-with-value-types"></a>Semântica de referência com tipos de valor

Recursos de idioma introduzidos no 7.2 permitem trabalhar com tipos de valor ao usar semântica de referência. Eles são projetados para melhorar o desempenho, minimizando a cópia de tipos de valor sem incorrer as alocações de memória associadas ao uso de tipos de referência. Os recursos incluem:

 - O `in` modificador em parâmetros para especificar que um argumento é passado por referência, mas não modificado pelo método chamado.
 - O `ref readonly` modificador no método retorna, para indicar que um método retorna seu valor por referência, mas não permite gravações para o objeto.
 - O `readonly struct` declaração, para indicar que uma struct é imutável e deve ser passada como um `in` parâmetro para seus métodos de membro.
 - O `ref struct` declaração, para indicar que um tipo struct acessa memória gerenciada diretamente e deve sempre ser pilha alocada.

Você pode ler mais sobre todas essas alterações em [com a semântica de referência de tipos de valor](../reference-semantics-with-value-types.md).

## <a name="non-trailing-named-arguments"></a>Argumentos nomeada à direita não

Chamadas de método agora podem usar argumentos nomeados que precedem argumentos posicionais quando esses argumentos nomeados são nas posições corretas. Para obter mais informações, consulte [nomeadas e argumentos opcionais](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Sublinhados em literais numéricos

A implementação de suporte para os separadores de dígitos no c# 7.0 não permite a `_` para ser o primeiro caractere do valor literal. Literais numéricos binários e hex agora podem começar com um `_`. 

Por exemplo:

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

Por fim, um novo modificador de acesso composta: `private protected` indica que um membro pode ser acessado por classes derivadas que são declaradas no mesmo assembly. Enquanto `protected internal` permite o acesso por classes derivadas ou classes que estão no mesmo assembly, `private protected` limita o acesso a tipos derivados declarado no mesmo assembly.

Para obter mais informações, consulte [modificadores de acesso](../language-reference/keywords/access-modifiers.md) na referência de linguagem.
