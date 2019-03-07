---
title: Método ICorDebugModule::GetMetaDataInterface
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5d28118ea1cc26f80ecc67ccedd160447aa69a4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479022"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>Método ICorDebugModule::GetMetaDataInterface
Obtém um objeto de interface de metadados que pode ser usado para examinar os metadados para o módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `riid`  
 [in] A ID de referência que especifica a interface de metadados.  
  
 `ppObj`  
 [out] Um ponteiro para o endereço de um `T:IUnknown` objeto que é um dos [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).  
  
## <a name="remarks"></a>Comentários  
 O depurador pode usar o `GetMetaDataInterface` método para fazer uma cópia dos metadados para um módulo, que deve ser feito para editar esse módulo original. As chamadas do depurador `GetMetaDataInterface` para obter uma [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) objeto de interface do módulo, em seguida, chama [imetadataemit:: Savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) para salvar uma cópia dos metadados do módulo para a memória.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Metadados](../../../../docs/framework/unmanaged-api/metadata/index.md)
