---
title: Interface IHostMalloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea3656fa00e84291ff7b2bdb65f9300cd7933c0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571776"
---
# <a name="ihostmalloc-interface"></a>Interface IHostMalloc
Fornece métodos que permitem que o common language runtime (CLR) para solicitar refinadas alocações do heap por meio do host.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|Solicita que o host alocar a quantidade solicitada de memória do heap.|  
|[Método DebugAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|Solicita que o host alocar a quantidade solicitada de memória do heap e, além disso, controlar em que a memória foi alocada.|  
|[Método Free](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|Libera a memória que foi alocada usando o `Alloc` método.|  
  
## <a name="remarks"></a>Comentários  
 O CLR obtém um ponteiro de interface para um `IHostMalloc` instância chamando o [ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
