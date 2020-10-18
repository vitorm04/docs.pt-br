---
title: A instrução não é válida dentro de um método/lambda de várias linhas
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: cef992c3eaa2b82bbf5e8993f9fccd64ae388c95
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159671"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a>BC30024: a instrução não é válida dentro de um método/lambda de várias linhas

A instrução não é válida dentro de `Sub` um `Function` procedimento,, propriedade `Get` ou propriedade `Set` . Algumas instruções podem ser colocadas no nível do módulo ou da classe. Outros, como `Option Strict` , devem estar no nível de namespace e preceder todas as outras declarações.

 **ID do erro:** BC30024

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Remova a instrução do procedimento.

## <a name="see-also"></a>Veja também

- [Instrução Sub](../statements/sub-statement.md)
- [Instrução Function](../statements/function-statement.md)
- [Instrução Get](../statements/get-statement.md)
- [Instrução SET](../statements/set-statement.md)
