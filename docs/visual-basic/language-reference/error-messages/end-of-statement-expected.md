---
title: "Fim de instrução esperado | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
dev_langs:
- VB
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 525f40f386a6a7a3e248a63d8724621c012f13b2
ms.lasthandoff: 03/13/2017

---
# <a name="end-of-statement-expected"></a>Fim de instrução esperado
A declaração é sintaticamente completa, mas um elemento de programação adicional vem depois do elemento que conclui a declaração. Um terminador de linha é necessário no final de cada instrução.  
  
 Um terminador de linha divide os caracteres de um arquivo de origem Visual Basic em linhas. Exemplos de terminadores de linha são o Unicode carro retorno caractere (< / HD), o Unicode avanço de linha caractere (< / HA), e o Unicode retorno de carro seguido de um caractere de avanço de linha Unicode do caractere. Para obter mais informações sobre os terminadores de linha, consulte o [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification.md).  
  
 **ID do erro:** BC30205  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se duas declarações diferentes foram inadvertidamente colocadas na mesma linha.  
  
2.  Insira um terminador de linha após o elemento que conclui a declaração.  
  
## <a name="see-also"></a>Consulte também  
 [Como: quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
