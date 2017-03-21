---
title: "Nenhum método &quot;Main&quot; acessível com uma assinatura apropriada foi encontrado em &quot;&lt;nome&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
dev_langs:
- VB
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9c036fbaaf7b634fba61516cb1455c6d7714b536
ms.lasthandoff: 03/13/2017

---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '&lt;nome&gt;'
Aplicativos de linha de comando devem ter um `Sub Main` definido. `Main`deve ser declarado como `Public Shared` se ele for definido em uma classe, ou como `Public` se definido em um módulo.  
  
 Para obter mais informações sobre `Main`, consulte [NIB: Visual Basic versão de Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c).  
  
 **ID do erro:** BC30737  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Definir uma `Public Sub Main` procedimento para seu projeto. Declare-o como `Shared` somente se você defini-lo dentro de uma classe.  
  
## <a name="see-also"></a>Consulte também  
 [NIB: versão do Visual Basic do Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)   
 [Estrutura de um programa Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
