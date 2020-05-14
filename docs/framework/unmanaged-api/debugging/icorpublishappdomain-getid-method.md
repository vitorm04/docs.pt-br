---
title: Método ICorPublishAppDomain::GetID
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
ms.openlocfilehash: 36c5c674f3cdf867107b9ee85a5befadc9246d78
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396313"
---
# <a name="icorpublishappdomaingetid-method"></a>Método ICorPublishAppDomain::GetID
Obtém o identificador exclusivo para este [ICorPublishAppDomain](icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `puId`  
 fora Um ponteiro para o identificador do domínio do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 O identificador é exclusivo somente no escopo do processo que o contém.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorPublishAppDomain](icorpublishappdomain-interface.md)
