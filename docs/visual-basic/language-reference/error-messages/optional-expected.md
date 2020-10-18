---
title: "'Optional' esperado"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 9c717cef2052722563e04595ef7a808ea103a75d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159814"
---
# <a name="bc30202-optional-expected"></a>BC30202: ' optional ' esperado

Um argumento opcional em uma declaração de procedimento é seguido por um argumento necessário. Todos os argumentos após um argumento opcional também devem ser opcionais.

 **ID do erro:** BC30202

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Se o argumento se destinar a ser necessário, mova-o para preceder o primeiro argumento opcional na lista de argumentos.

- Se o argumento se destinar a ser opcional, use a `Optional` palavra-chave.

## <a name="see-also"></a>Veja também

- [Parâmetros Opcionais](../../programming-guide/language-features/procedures/optional-parameters.md)
