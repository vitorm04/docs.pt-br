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
ms.openlocfilehash: 715ff5d4a06b53361d550f04e5154023d0b641bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095117"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>Método ICorDebugILFrame2::EnumerateTypeParameters
Obtém um objeto ICorDebugTypeEnum que contém os parâmetros de <xref:System.Type> neste quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppTyParEnum`  
 Um ponteiro para o endereço de um objeto de interface ICorDebugTypeEnum que permite a enumeração de parâmetros de tipo.  
  
 A lista de parâmetros de tipo inclui os parâmetros de tipo de classe (se houver) seguidos pelos parâmetros de tipo de método (se houver).  
  
## <a name="remarks"></a>Comentários  
 Use o método [IMetaDataImport2:: EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) para determinar quantos parâmetros de tipo de classe e parâmetros de tipo de método essa lista contém.  
  
 Os parâmetros de tipo nem sempre estão disponíveis.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
