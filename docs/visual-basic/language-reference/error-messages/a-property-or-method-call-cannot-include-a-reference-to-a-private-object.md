---
title: Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 00237d795fb62fbae426e0015d8e64d5fabb4c32
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162668"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno

Entre as possíveis causas desse erro estão:

- Um cliente invocou uma propriedade ou um método de um componente fora do processo e tentou passar uma referência a um objeto particular como um dos argumentos.

- Um componente fora do processo chamou um método de retorno de chamada em seu cliente e tentou passar uma referência a um objeto particular.

- Um componente fora do processo tentou passar uma referência a um objeto particular como um argumento de um evento que ele estava gerando.

- Um cliente tentou atribuir uma referência de objeto particular a um `ByRef` argumento de um evento que ele estava manipulando.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Remova a referência.

## <a name="see-also"></a>Veja também

- [Privado](../modifiers/private.md)
