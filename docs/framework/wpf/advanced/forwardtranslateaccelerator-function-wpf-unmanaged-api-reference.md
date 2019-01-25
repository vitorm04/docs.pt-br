---
title: Função ForwardTranslateAccelerator (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 78031ed80fe83b736a351886457f9200534f470b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591507"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>Função ForwardTranslateAccelerator (referência de API não gerenciada WPF)
Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.  
  
 Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento do windows.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pMsg  
 Um ponteiro para uma mensagem.  
  
 appUnhandled  
 `true` Quando o aplicativo já tem a oportunidade de manipular a mensagem de entrada, mas não tratada. Caso contrário, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Ver [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400.dll  
  
 **Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Referência de API não gerenciada do WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
