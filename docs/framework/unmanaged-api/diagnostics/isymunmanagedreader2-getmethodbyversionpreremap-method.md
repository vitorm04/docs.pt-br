---
title: Método ISymUnmanagedReader2::GetMethodByVersionPreRemap
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e84d912a96752a893230393b59496377b783956
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494906"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a>Método ISymUnmanagedReader2::GetMethodByVersionPreRemap
Obtém um método de leitor de símbolo, considerando um token de método e um número de versão de editar e continuar. Números de versão começam em 1 e são incrementados sempre que o método é alterado como resultado de uma operação de editar e continuar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `token`  
 [in] O token de metadados do método.  
  
 `version`  
 [in] A versão do método.  
  
 `pRetVal`  
 [out] Um ponteiro para retornado [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl. CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedReader2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
