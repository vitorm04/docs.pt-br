---
title: Instrução Throw
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352790"
---
# <a name="throw-statement-visual-basic"></a>Instrução Throw (Visual Basic)

Gera uma exceção em um procedimento.

## <a name="syntax"></a>Sintaxe

```vb
Throw [ expression ]
```

## <a name="part"></a>Parte

`expression`\
Fornece informações sobre a exceção a ser gerada. Opcional ao residir em uma instrução `Catch`, caso contrário, é necessário.

## <a name="remarks"></a>Comentários

A instrução `Throw` gera uma exceção que você pode manipular com código de manipulação de exceção estruturado (`Try`...`Catch`...`Finally`) ou código de tratamento de exceção não estruturado (`On Error GoTo`). Você pode usar a instrução `Throw` para interceptar erros em seu código porque Visual Basic move para cima a pilha de chamadas até encontrar o código de tratamento de exceção apropriado.

Uma instrução `Throw` sem expressão só pode ser usada em uma instrução `Catch`; nesse caso, a instrução gera novamente a exceção que está sendo manipulada pela instrução `Catch`.

A instrução `Throw` redefine a pilha de chamadas para a exceção `expression`. Se `expression` não for fornecido, a pilha de chamadas permanecerá inalterada. Você pode acessar a pilha de chamadas para a exceção por meio da propriedade <xref:System.Exception.StackTrace%2A>.

## <a name="example"></a>Exemplo

O código a seguir usa a instrução `Throw` para gerar uma exceção:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Consulte também

- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
