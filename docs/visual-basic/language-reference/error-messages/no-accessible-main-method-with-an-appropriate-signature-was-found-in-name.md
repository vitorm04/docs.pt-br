---
title: Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 559c905d1e2e2de4500771a93d6116f9630011ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591990"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '\<nome >'
Aplicativos de linha de comando devem ter um `Sub Main` definido. `Main` deve ser declarado como `Public Shared` se ela é definida em uma classe, ou como `Public` se definida em um módulo.  
  
 **ID do erro:** BC30737  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Definir um `Public Sub Main` procedimento para seu projeto. Declare-o como `Shared` se e somente se você defini-lo dentro de uma classe.  
  
## <a name="see-also"></a>Consulte também

- [Estrutura de um programa Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
