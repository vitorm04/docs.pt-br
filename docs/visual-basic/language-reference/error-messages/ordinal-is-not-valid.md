---
title: "Ordinal não é válido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID452
dev_langs:
- VB
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: 8
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
ms.openlocfilehash: 2add456dc1a40e442dedb4d6901872690a549e7f
ms.lasthandoff: 03/13/2017

---
# <a name="ordinal-is-not-valid"></a>O ordinal não é válido
Sua chamada para uma biblioteca de vínculo dinâmico (DLL) indicada usa um número em vez de um nome de procedimento, usando o `#num` sintaxe. Este erro possui as seguintes causas possíveis:  
  
-   Uma tentativa de converter o `#num` expressão a um ordinal falhou.  
  
-   O `#num` especificado não especifica qualquer função na DLL.  
  
-   Uma biblioteca de tipos tem uma declaração inválida resultando em uso interno do número ordinal inválido.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se que a expressão representa um número válido, ou chame o procedimento por nome.  
  
2.  Certifique-se de `#num` identifica uma função válida no DLL.  
  
3.  Isole a chamada de procedimento causando o problema comentando o código. Escrever um `Declare` declaração de procedimento e relatar o problema para o fornecedor da biblioteca de tipo.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
