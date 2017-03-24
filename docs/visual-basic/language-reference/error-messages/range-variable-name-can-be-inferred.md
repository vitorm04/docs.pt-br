---
title: "Nome de variável de intervalo pode ser inferido somente de um nome simple ou qualificado sem argumentos | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36599
- bc36599
dev_langs:
- VB
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: 6
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
ms.openlocfilehash: 830a4e9f072139ba31ac4958748aff2eaba39e3b
ms.lasthandoff: 03/13/2017

---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>O nome da variável de intervalo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos
Um elemento de programação que usa um ou mais argumentos está incluído em uma consulta LINQ. O compilador é capaz de inferir a uma variável de intervalo do elemento de programação.  
  
 **ID do erro:** BC36599  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Forneça um nome de variável explícito para o elemento de programação, conforme mostrado no código a seguir:  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
