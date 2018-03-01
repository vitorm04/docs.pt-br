---
title: "Não acessível &#39; Principal &#39; método com uma assinatura apropriada foi encontrado em &#39; &lt;nome&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6a2d66c860b72bd3ef59c02f548ac563fab6b8c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Não acessível &#39; Principal &#39; método com uma assinatura apropriada foi encontrado em &#39; &lt;nome&gt;&#39;
Aplicativos de linha de comando devem ter um `Sub Main` definido. `Main`deve ser declarado como `Public Shared` se ele é definido em uma classe ou como `Public` se definido em um módulo.  
  
 **ID do erro:** BC30737  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Definir um `Public Sub Main` procedimento para seu projeto. Declare-o como `Shared` somente se você defini-lo dentro de uma classe.  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura de um programa do Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
