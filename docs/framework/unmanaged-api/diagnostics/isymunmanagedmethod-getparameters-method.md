---
title: Método ISymUnmanagedMethod::GetParameters
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0fc5fd29b8b423ddd3a659ee2fc8a339eea0105
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733877"
---
# <a name="isymunmanagedmethodgetparameters-method"></a>Método ISymUnmanagedMethod::GetParameters
Obtém os parâmetros para esse método. Os parâmetros são retornados na ordem em que eles são definidos dentro da assinatura do método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cParams`  
 [in] O tamanho do `params` matriz.  
  
 `pcParams`  
 [in] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer que é necessário para conter os parâmetros.  
  
 `params`  
 [out] Um ponteiro para o buffer que recebe os parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
