---
title: Operador -&gt; – Referência de C#
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: bb1ccd026f403e68565c5c7681943d8017578d01
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234884"
---
# <a name="-gt-operator-c-reference"></a>Operador -&gt; (Referência de C#)

O operador de acesso de membro de ponteiro `->` combina a indireção do ponteiro e o acesso de membro.

Se `x` é um ponteiro do tipo `T*` e `y` é um membro acessível de `T`, uma expressão do formulário

```csharp
x->y
```

equivale a

```csharp
(*x).y
```

O operador `->` requer contexto [não seguro](../keywords/unsafe.md).

Para saber mais, confira [Como acessar um membro com um ponteiro](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

O operador `->` não pode ser sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [Acesso de membro de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-member-access) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
