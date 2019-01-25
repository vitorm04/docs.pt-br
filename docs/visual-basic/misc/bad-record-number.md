---
title: Número de registro inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: fbf1a2db97d0474fb758ff5ed572e94395a187da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664741"
---
# <a name="bad-record-number"></a>Número de registro inválido
O número de registro em `a FileGet`, `FilePut`, `FileGetObject`, ou `FilePutObject` instrução é menor ou igual a zero.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique os cálculos usados para gerar o número do registro. Verifique a ortografia das variáveis que contém o número de registro ou usado no cálculo de números de registro. Um nome de variável digitado incorretamente é implicitamente declarado e inicializado como zero, a menos que você usou `Option Explicit On` no módulo.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Option Explicit](../../visual-basic/language-reference/statements/option-explicit-statement.md)
