---
title: Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: e1f95484a153bdcac9543508b7f2708dc6b7d942
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160035"
---
# <a name="bc30737-no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>BC30737: nenhum método ' Main ' acessível com uma assinatura apropriada foi encontrado em ' \<name> '

Os aplicativos de linha de comando devem ter um `Sub Main` definido. `Main` deve ser declarado como `Public Shared` se fosse definido em uma classe, ou como `Public` se estiver definido em um módulo.

 **ID do erro:** BC30737

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Defina um `Public Sub Main` procedimento para seu projeto. Declare-a como `Shared` If e only se você defini-la dentro de uma classe.

## <a name="see-also"></a>Veja também

- [Estrutura de um programa Visual Basic](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procedimentos](../../programming-guide/language-features/procedures/index.md)
