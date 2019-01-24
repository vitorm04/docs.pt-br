---
title: Estrutura StackOverflowInfo
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c1723facca3c547c275ee44f0abefe21a177eb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572023"
---
# <a name="stackoverflowinfo-structure"></a>Estrutura StackOverflowInfo
Armazena o tipo de estouro que ocorreram e informações sobre a exceção que foi gerada devido ao estouro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`soType`|Um valor igual a [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeração que especifica o tipo de estouro.|  
|`pExceptionInfo`|Um ponteiro para um Win32 `EXCEPTION_POINTERS` objeto, que contém um registro de exceção com uma descrição independente de máquina de uma exceção e um registro de contexto com uma descrição de máquina dependente de contexto do processador no momento da exceção.|  
  
## <a name="remarks"></a>Comentários  
 Um `StackOverflowInfo` objeto é passado para o [iactiononclrevent:: ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método para `Event_StackOverflow` eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
