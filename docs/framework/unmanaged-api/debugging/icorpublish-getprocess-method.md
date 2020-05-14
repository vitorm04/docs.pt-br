---
title: Método ICorPublish::GetProcess
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: 2cd2238ac67713564922be440ce64a2ebc4bbf44
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396328"
---
# <a name="icorpublishgetprocess-method"></a>Método ICorPublish::GetProcess
Obtém uma instância de [ICorPublishProcess](icorpublishprocess-interface.md) que representa o processo com o identificador especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pid`  
 no O identificador do processo.  
  
 `ppProcess`  
 fora Um ponteiro para o endereço de uma `ICorPublishProcess` instância que representa o processo.  
  
## <a name="remarks"></a>Comentários  
 `GetProcess`falhará se o processo não existir ou não for um processo gerenciado que possa ser depurado pelo usuário atual.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorPublish](icorpublish-interface.md)
