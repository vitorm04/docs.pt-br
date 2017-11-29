---
title: "Função ClrCreateManagedInstance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: ClrCreateManagedInstance
helpviewer_keywords: ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d27a881f84121f0d096eae7c693dec5b674caec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="clrcreatemanagedinstance-function"></a>Função ClrCreateManagedInstance
Cria uma instância do tipo gerenciado especificado.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Usar ativação COM para criar uma instância do tipo gerenciado, ou usar a hospedagem (consulte [CLR Interfaces de hospedagem adicionadas no .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pTypeName`  
 [in] Um ponteiro para o nome do tipo de instância que está sendo solicitado.  
  
 `riid`  
 [in] O `IID` do tipo de instância que está sendo solicitado.  
  
 `ppObject`  
 [out] Um ponteiro para um ponteiro para uma instância do tipo gerenciado que foi solicitado pelo chamador.  
  
## <a name="remarks"></a>Comentários  
 O common language runtime já deve ser carregado em um processo. Por exemplo, pode ser carregado por meio de uma chamada para o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) função antes do `ClrCreateManagedInstance` função é chamada. Se o tempo de execução não está carregado, `ClrCreateManagedInstance` primeiro tenta carregar v 1.0.3705 do tempo de execução. Se isso falhar, ele tenta carregar a versão mais recente do tempo de execução.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
