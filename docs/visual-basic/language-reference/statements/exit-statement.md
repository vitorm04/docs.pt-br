---
title: Instrução Exit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 9c25653809c51662ea5b606ab97be6a9b50d5986
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956943"
---
# <a name="exit-statement-visual-basic"></a>Instrução Exit (Visual Basic)

Sai de um procedimento ou bloco e transfere o controle imediatamente para a instrução após a chamada de procedimento ou a definição de bloco.

## <a name="syntax"></a>Sintaxe

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a>Instruções

 `Exit Do`  
 Sai imediatamente do loop `Do` no qual ele aparece. A execução continua com a instrução após a instrução `Loop`. `Exit Do` pode ser usado somente dentro de um loop `Do`. Quando usado em loops `Do` aninhados, `Exit Do` sai do loop mais interno e transfere o controle para o próximo nível mais alto de aninhamento.

 `Exit For`  
 Sai imediatamente do loop `For` no qual ele aparece. A execução continua com a instrução após a instrução `Next`. `Exit For` só pode ser usado dentro de um loop `For`... `Next` ou `For Each`... `Next`. Quando usado em loops `For` aninhados, `Exit For` sai do loop mais interno e transfere o controle para o próximo nível mais alto de aninhamento.

 `Exit Function`  
 Sai imediatamente do procedimento `Function` no qual ele aparece. A execução continua com a instrução após a instrução que chamou o procedimento `Function`. `Exit Function` só pode ser usado dentro de um procedimento `Function`.

 Para especificar um valor de retorno, você pode atribuir o valor ao nome da função em uma linha antes da instrução `Exit Function`. Para atribuir o valor de retorno e sair da função em uma instrução, em vez disso, você pode usar a [instrução return](return-statement.md).

 `Exit Property`  
 Sai imediatamente do procedimento `Property` no qual ele aparece. A execução continua com a instrução que chamou o procedimento `Property`, ou seja, com a instrução solicitando ou definindo o valor da propriedade. `Exit Property` só pode ser usado dentro de um procedimento `Get` ou `Set` de uma propriedade.

 Para especificar um valor de retorno em um procedimento `Get`, você pode atribuir o valor ao nome da função em uma linha antes da instrução `Exit Property`. Para atribuir o valor de retorno e sair do procedimento `Get` em uma instrução, em vez disso, você pode usar a instrução `Return`.

 Em um procedimento `Set`, a instrução `Exit Property` é equivalente à instrução `Return`.

 `Exit Select`  
 Sai imediatamente do bloco `Select Case` no qual ele aparece. A execução continua com a instrução após a instrução `End Select`. `Exit Select` pode ser usado somente dentro de uma instrução `Select Case`.

 `Exit Sub`  
 Sai imediatamente do procedimento `Sub` no qual ele aparece. A execução continua com a instrução após a instrução que chamou o procedimento `Sub`. `Exit Sub` só pode ser usado dentro de um procedimento `Sub`.

 Em um procedimento `Sub`, a instrução `Exit Sub` é equivalente à instrução `Return`.

 `Exit Try`  
 Sai imediatamente do bloco `Try` ou `Catch` no qual ele aparece. A execução continua com o bloco `Finally` se houver um, ou com a instrução após a instrução `End Try`, caso contrário. `Exit Try` pode ser usado somente dentro de um bloco `Try` ou `Catch` e não dentro de um bloco `Finally`.

 `Exit While`  
 Sai imediatamente do loop `While` no qual ele aparece. A execução continua com a instrução após a instrução `End While`. `Exit While` pode ser usado somente dentro de um loop `While`. Quando usado em loops `While` aninhados, o `Exit While` transfere o controle para o loop que é um nível aninhado acima do loop onde `Exit While` ocorre.

## <a name="remarks"></a>Comentários

Não confunda instruções `Exit` com instruções `End`. `Exit` não define o fim de uma instrução.

## <a name="example"></a>Exemplo

No exemplo a seguir, a condição de loop para o loop quando a variável `index` é maior que 100. No entanto, a instrução `If` no loop faz com que a instrução `Exit Do` Pare o loop quando a variável de índice é maior que 10.

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a>Exemplo

O exemplo a seguir atribui o valor de retorno ao nome da função `myFunction` e, em seguida, usa `Exit Function` para retornar da função:

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a>Exemplo

O exemplo a seguir usa a [instrução return](return-statement.md) para atribuir o valor de retorno e sair da função:

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a>Consulte também

- [Instrução Continue](continue-statement.md)
- [Instrução Do...Loop](do-loop-statement.md)
- [Instrução End](end-statement.md)
- [Instrução For Each...Next](for-each-next-statement.md)
- [Instrução For...Next](for-next-statement.md)
- [Instrução Function](function-statement.md)
- [Instrução Return](return-statement.md)
- [Instrução Stop](stop-statement.md)
- [Instrução Sub](sub-statement.md)
- [Instrução Try...Catch...Finally](try-catch-finally-statement.md)
