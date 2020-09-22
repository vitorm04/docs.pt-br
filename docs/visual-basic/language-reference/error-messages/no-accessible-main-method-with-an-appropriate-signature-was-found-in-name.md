---
title: Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6958e778701066760aa74e3b4d566800b7527b76
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871479"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '\<name>'

Os aplicativos de linha de comando devem ter um `Sub Main` definido. `Main` deve ser declarado como `Public Shared` se fosse definido em uma classe, ou como `Public` se estiver definido em um módulo.  
  
 **ID do erro:** BC30737  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Defina um `Public Sub Main` procedimento para seu projeto. Declare-a como `Shared` If e only se você defini-la dentro de uma classe.  
  
## <a name="see-also"></a>Confira também

- [Estrutura de um programa Visual Basic](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procedimentos](../../programming-guide/language-features/procedures/index.md)
