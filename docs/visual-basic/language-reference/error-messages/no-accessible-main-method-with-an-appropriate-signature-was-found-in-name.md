---
title: "Não acessível &#39; Principal &#39; método com uma assinatura apropriada foi encontrado em &#39; &lt;nome&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords: BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f45dc17304c3c9d62b65760f2c1b5d461812a66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Não acessível &#39; Principal &#39; método com uma assinatura apropriada foi encontrado em &#39; &lt;nome&gt;&#39;
Aplicativos de linha de comando devem ter um `Sub Main` definido. `Main`deve ser declarado como `Public Shared` se ele é definido em uma classe ou como `Public` se definido em um módulo.  
  
 Para obter mais informações sobre `Main`, consulte [NIB: Visual Basic versão de Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c).  
  
 **ID do erro:** BC30737  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Definir um `Public Sub Main` procedimento para seu projeto. Declare-o como `Shared` somente se você defini-lo dentro de uma classe.  
  
## <a name="see-also"></a>Consulte também  
 [NIB: versão do Visual Basic do Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [Estrutura de um programa do Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
