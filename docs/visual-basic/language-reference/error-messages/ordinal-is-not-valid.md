---
title: "O ordinal não é válido"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ordinal-is-not-valid"></a>O ordinal não é válido
A chamada para uma biblioteca de vínculo dinâmico (DLL) indicado para usar um número em vez de um nome de procedimento, usando o `#num` sintaxe. Esse erro tem as seguintes causas possíveis:  
  
-   Uma tentativa de converter o `#num` expressão a um ordinal falhou.  
  
-   O `#num` especificado não especifica qualquer função na DLL.  
  
-   Uma biblioteca de tipos tem uma declaração inválida resultando no uso interno de um número ordinal inválido.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se que a expressão representa um número válido, ou chame o procedimento por nome.  
  
2.  Certifique-se de `#num` identifica uma função válida no DLL.  
  
3.  Isole a causa do problema comentando o código de chamada de procedimento. Gravar um `Declare` instrução para o procedimento e relatar o problema para o fornecedor da biblioteca de tipo.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
