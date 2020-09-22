---
title: A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 5e75c29e57a9c04c66e6bca79d99bb18c513f667
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870740"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha

Uma `If` instrução de linha única contém várias instruções separadas por dois-pontos (:), uma das quais é uma `End` instrução para um bloco de controle fora da linha única `If` . `If`Instruções de linha única não usam a `End If` instrução.  
  
 **ID do erro:** BC32005  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Mova a instrução de linha única para `If` fora do bloco de controle que contém a `End If` instrução.  
  
## <a name="see-also"></a>Confira também

- [Instrução If...Then...Else](../statements/if-then-else-statement.md)
