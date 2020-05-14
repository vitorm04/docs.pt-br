---
title: Método ICorPublishAppDomain::GetName
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: e95f96847c6e069758362fb6febc28dc31911bc9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396291"
---
# <a name="icorpublishappdomaingetname-method"></a>Método ICorPublishAppDomain::GetName
Obtém o nome do domínio do aplicativo que é representado por este [ICorPublishAppDomain](icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchName`  
 no O tamanho da `szName` matriz.  
  
 `pcchName`  
 fora Um ponteiro para o número de caracteres largos, incluindo o caractere nulo, retornado na `szName` matriz.  
  
 `szName`  
 fora Uma matriz na qual armazenar o nome.  
  
## <a name="remarks"></a>Comentários  
 Se `szName` for não nulo, o `GetName` método copiará até `cchName` caracteres (incluindo o terminador nulo) para o `szName` . Se um não nulo for retornado em `pcchName` , o número real de caracteres no nome (incluindo o terminador nulo) será armazenado na `szName` matriz.  
  
 O `GetName` método retorna um S_OK HRESULT, independentemente de quantos caracteres foram copiados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorPublishAppDomain](icorpublishappdomain-interface.md)
