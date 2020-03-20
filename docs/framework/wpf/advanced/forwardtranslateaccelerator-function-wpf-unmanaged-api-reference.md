---
title: Função ForwardTranslateAccelerator - Referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186628"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>Função ForwardTranslateAccelerator (referência de API não gerenciada WPF)
Esta API suporta a infra-estrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.  
  
 Usado pela infra-estrutura do Windows Presentation Foundation (WPF) para gerenciamento de janelas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>parâmetros  
 pMsg  
 Um ponteiro para uma mensagem.  
  
 appUnhandled  
 `true`quando o aplicativo já teve a chance de lidar com a mensagem de entrada, mas não a lidou com ela; caso contrário, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Consulte [os requisitos do sistema de estrutura .NET](../../get-started/system-requirements.md).  
  
 **Dll:**  
  
 No quadro .NET 3.0 e 3.5: PresentationHostDLL.dll  
  
 No Quadro .NET 4 e posteriores: PresentationHost_v0400.dll  
  
 **.NET Framework Version:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
