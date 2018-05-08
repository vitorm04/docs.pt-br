---
title: Método IAssemblyCache::CreateAssemblyCacheItem
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c45257a76127adf2bcf9ab356639d4754d151bf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a>Método IAssemblyCache::CreateAssemblyCacheItem
Obtém uma referência a um novo [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFlags`  
 [in] Sinalizadores definidos no Fusion.idl. Há suporte para os seguintes valores:  
  
-   IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)  
  
-   IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)  
  
 `pvReserved`  
 [in] Reservado para extensibilidade futura. `pvReserved` deve ser uma referência nula.  
  
 `ppAsmItem`  
 [out] Retornado `IAssemblyCacheItem` ponteiro.  
  
 `pszAssemblyName`  
 [in, opcional] Uncanonicalized, separados por vírgulas `name=value` pares.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [Interface IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
