---
title: '* Operador – referência do C#'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333727"
---
# <a name="-operator-c-reference"></a>Operador * (referência do C#)

O operador de multiplicação (`*`) calcula o produto dos operandos. Todos os tipos numéricos têm operadores de multiplicação predefinidos.

`*` também atua como o operador de desreferenciamento, que permite a leitura e a gravação em um ponteiro.

## <a name="remarks"></a>Comentários

O operador `*` também é usado para declarar tipos de ponteiro e para desreferenciar ponteiros. Esse operador pode ser usado somente em contextos não seguros, indicado pelo uso da palavra-chave [unsafe](../keywords/unsafe.md) e exigindo a opção do compilador [/unsafe](../compiler-options/unsafe-compiler-option.md).  O operador de desreferenciamento é também conhecido como operador de indireção.

Tipos definidos pelo usuário podem sobrecarregar o operador binário `*` (consulte [operador](../keywords/operator.md)). Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.

## <a name="example"></a>Exemplo

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md)
- [Operadores do C#](index.md)