---
title: Método ICorPublishProcess::IsManaged
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 68931ba16ea1f8f61176c6d6ed8300e762b61690
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790535"
---
# <a name="icorpublishprocessismanaged-method"></a>Método ICorPublishProcess::IsManaged
Obtém um valor que indica se o processo referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md) é conhecido por ter código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pbManaged`  
 fora Um ponteiro para um valor booliano que indica se o processo tem código gerenciado. O valor será `true` se o processo tiver código gerenciado; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Como a versão atual do `ICorPublishProcess` permite o acesso apenas a processos que têm código gerenciado, `IsManaged` sempre retorna `true`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorPublishProcess](icorpublishprocess-interface.md)
