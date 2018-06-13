---
title: Método ISymUnmanagedConstant::GetSignature
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce9ce768e32434e0a1acd2fad67a0cdc99f49e18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430140"
---
# <a name="isymunmanagedconstantgetsignature-method"></a>Método ISymUnmanagedConstant::GetSignature
Obtém a assinatura da constante.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cSig`  
 [in] O comprimento do buffer que o `pcSig` parâmetro aponta para.  
  
 `pcSig`  
 [out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter a assinatura.  
  
 `sig`  
 [out] O buffer que armazena a assinatura.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedConstant](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [Método GetName](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [Método GetValue](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
