---
title: '&#39;Dir&#39; função deve ser chamada primeiro com um &#39;PathName&#39; argumento'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: f7e9ef9cc6309f24ae9f8963e910b41180c029b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518482"
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39;Dir&#39; função deve ser chamada primeiro com um &#39;PathName&#39; argumento
Uma chamada inicial para o `Dir` função não inclui o `PathName` argumento. A primeira chamada para `Dir` deve incluir uma `PathName`, as chamadas subsequentes, mas para `Dir` não precisa incluir parâmetros para recuperar o próximo item.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Forneça um `PathName` argumento na chamada de função.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
