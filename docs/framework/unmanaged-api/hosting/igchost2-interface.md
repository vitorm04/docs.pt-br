---
title: Interface IGCHost2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost2
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost2
helpviewer_keywords: IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6706696e3fd5158d2b49a4d114d978a26510b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="igchost2-interface"></a>Interface IGCHost2
Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.  
  
> [!NOTE]
>  Para novos desenvolvimentos, recomendamos que você use o [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface em vez disso.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|Define o tamanho do segmento e o tamanho máximo de geração 0. Habilita a geração 0 e tamanhos de segmento maior do que `DWORD`.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** GCHost.idl, GCHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Interfaces de hospedagem CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Coclass CorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
