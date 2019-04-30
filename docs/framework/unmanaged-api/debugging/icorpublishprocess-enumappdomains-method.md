---
title: Método ICorPublishProcess::EnumAppDomains
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 173a7d6793bec9262efb661d56e3a371d0bf9b47
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986616"
---
# <a name="icorpublishprocessenumappdomains-method"></a>Método ICorPublishProcess::EnumAppDomains
Obtém um enumerador para os domínios de aplicativo no processo que é referenciado por este [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Um ponteiro para o endereço de um [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instância que permite iteração por meio da coleção de domínios de aplicativo nesse processo.  
  
## <a name="remarks"></a>Comentários  
 A lista de domínios de aplicativo baseia-se em um instantâneo dos domínios de aplicativo existe quando o `EnumAppDomains` método é chamado. Esse método pode ser chamado mais de uma vez para criar uma nova lista atualizada. Listas existentes não serão afetadas por chamadas subsequentes desse método.  
  
 Se o processo foi encerrado, `EnumAppDomains` falhará com um valor HRESULT de CORDBG_E_PROCESS_TERMINATED.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub.idl, CorPub.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
