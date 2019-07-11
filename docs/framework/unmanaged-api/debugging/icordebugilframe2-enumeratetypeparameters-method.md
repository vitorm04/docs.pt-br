---
title: Método ICorDebugILFrame2::EnumerateTypeParameters
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2e53bfb46579cc51b7ad88ef7de2b9f8d2f9390
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758759"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>Método ICorDebugILFrame2::EnumerateTypeParameters
Obtém um objeto ICorDebugTypeEnum que contém o <xref:System.Type> parâmetros neste quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppTyParEnum`  
 Um ponteiro para o endereço de um objeto de interface ICorDebugTypeEnum que permite que a enumeração dos parâmetros de tipo.  
  
 A lista de parâmetros de tipo incluem os classe parâmetros de tipo (se houver) seguidos pelos parâmetros de tipo de método (se houver).  
  
## <a name="remarks"></a>Comentários  
 Use o [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) método para determinar quantos parâmetros de tipo de classe e método contém esta lista de parâmetros de tipo.  
  
 Os parâmetros de tipo não estão sempre disponíveis.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
