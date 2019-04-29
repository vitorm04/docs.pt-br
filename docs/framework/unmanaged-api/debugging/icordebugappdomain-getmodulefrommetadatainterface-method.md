---
title: Método ICorDebugAppDomain::GetModuleFromMetaDataInterface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eaa48dcc7dad2d66f1a60922c94193120b59b32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785147"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a>Método ICorDebugAppDomain::GetModuleFromMetaDataInterface
Obtém o módulo que corresponda à interface de metadados especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pIMetaData`  
 [in] Um ponteiro para um objeto que é um dos [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).  
  
 `ppModule`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo correspondente para a interface de metadados especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
