---
title: A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 4fd7577accd0b312ee1e3d2d990d256514d5f5f6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161329"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>BC32005: a instrução não pode encerrar um bloco fora de uma instrução ' If ' de linha

Uma `If` instrução de linha única contém várias instruções separadas por dois-pontos (:), uma das quais é uma `End` instrução para um bloco de controle fora da linha única `If` . `If`Instruções de linha única não usam a `End If` instrução.

 **ID do erro:** BC32005

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Mova a instrução de linha única para `If` fora do bloco de controle que contém a `End If` instrução.

## <a name="see-also"></a>Veja também

- [Instrução If...Then...Else](../statements/if-then-else-statement.md)
