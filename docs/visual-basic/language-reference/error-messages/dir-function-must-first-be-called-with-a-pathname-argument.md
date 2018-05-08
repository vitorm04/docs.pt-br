---
title: '&#39;Dir&#39; função deve ser chamada primeiro com um &#39;PathName&#39; argumento'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 3a271d7c2c2f7b98bae8f3f6fa9b67b65e3548f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39;Dir&#39; função deve ser chamada primeiro com um &#39;PathName&#39; argumento
Uma chamada inicial para o `Dir` função não inclui o `PathName` argumento. A primeira chamada para `Dir` deve incluir um `PathName`, mas subsequentes chamadas para `Dir` não precisa incluir parâmetros para recuperar o próximo item.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Forneça um `PathName` argumento na chamada de função.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
