---
title: Não acessível &#39;principal&#39; método com uma assinatura apropriada foi encontrado em &#39; &lt;nome&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6a60e26a2bd0e31c0f92dbbfb2518c75f304d9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Não acessível &#39;principal&#39; método com uma assinatura apropriada foi encontrado em &#39; &lt;nome&gt;&#39;
Aplicativos de linha de comando devem ter um `Sub Main` definido. `Main` deve ser declarado como `Public Shared` se ele é definido em uma classe ou como `Public` se definido em um módulo.  
  
 **ID do erro:** BC30737  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Definir um `Public Sub Main` procedimento para seu projeto. Declare-o como `Shared` somente se você defini-lo dentro de uma classe.  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura de um programa do Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
