---
title: Interface ICLRProbingAssemblyEnum
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c295a5633dedf1f0c85a9a697fea5524ee03fafc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432692"
---
# <a name="iclrprobingassemblyenum-interface"></a>Interface ICLRProbingAssemblyEnum
Fornece métodos que permitem que o host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que é internas para o common language runtime (CLR), sem a necessidade de criar ou entender que a identidade.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Get](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|Obtém a identidade do assembly no índice especificado.|  
  
## <a name="remarks"></a>Comentários  
 Métodos como [: Getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retornar um `ICLRProbingAssemblyEnum` instância.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
