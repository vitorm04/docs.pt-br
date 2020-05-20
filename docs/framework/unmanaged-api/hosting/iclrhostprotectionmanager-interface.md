---
title: Interface ICLRHostProtectionManager
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: 7b1fc70380fff3c551c56043f49c2deda507e366
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703845"
---
# <a name="iclrhostprotectionmanager-interface"></a>Interface ICLRHostProtectionManager
Permite que o host bloqueie classes gerenciadas, métodos, propriedades e campos específicos da execução em código parcialmente confiável.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[SetEagerSerializeGrantSets](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|Fornece uma garantia de que certas condições raras de corrida que podem causar erros fatais de Common Language Runtime (CLR) nunca surgirão.|  
|[Método SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md)|Especifica as categorias de tipos gerenciados e membros que devem ser impedidos de serem executados em código parcialmente confiável.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Enumeração EApiCategories](eapicategories-enumeration.md)
- [Interface ICLRControl](iclrcontrol-interface.md)
