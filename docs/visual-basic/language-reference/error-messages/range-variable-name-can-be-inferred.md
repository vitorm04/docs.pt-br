---
title: O nome da variável de intervalo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6d082511d501b961b537317f0cb17bcd1c9370b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594615"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>O nome da variável de intervalo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos
Um elemento de programação que usa um ou mais argumentos é incluído em uma consulta LINQ. O compilador é não é possível inferir uma variável de intervalo do elemento de programação.  
  
 **ID do erro:** BC36599  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Forneça um nome de variável explícito para o elemento de programação, como mostrado no código a seguir:  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
