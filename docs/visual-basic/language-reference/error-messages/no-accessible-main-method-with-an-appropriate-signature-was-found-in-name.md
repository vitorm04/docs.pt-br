---
title: Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: f5053bddf4b9ba791ad6d0733e1dd89c4ded91bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918262"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '\<nome >'
Aplicativos de linha de comando devem ter um `Sub Main` definido. `Main` deve ser declarado como `Public Shared` se ela é definida em uma classe, ou como `Public` se definida em um módulo.  
  
 **ID do erro:** BC30737  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Definir um `Public Sub Main` procedimento para seu projeto. Declare-o como `Shared` se e somente se você defini-lo dentro de uma classe.  
  
## <a name="see-also"></a>Consulte também

- [Estrutura de um programa Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
