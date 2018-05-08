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
ms.openlocfilehash: 8ab9773a5056dbfba422a9a53c7cd877e4c29abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a>Método ICorDebugAppDomain::GetModuleFromMetaDataInterface
Obtém o módulo que corresponda à interface de metadados fornecidos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pIMetaData`  
 [in] Um ponteiro para um objeto que é uma da [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).  
  
 `ppModule`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo correspondente à interface de metadados fornecidos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
