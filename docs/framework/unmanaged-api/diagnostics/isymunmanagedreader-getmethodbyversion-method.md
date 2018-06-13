---
title: Método ISymUnmanagedReader::GetMethodByVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef5888c33e9532e5fc132fe571d59699d6f80c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425162"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a>Método ISymUnmanagedReader::GetMethodByVersion
Obtém um método de leitor de símbolo, considerando um token de método e um número de versão de editar e copiar. Números de versão começam em 1 e são incrementados cada vez que o método é alterado como resultado de uma operação de cópia e de edição.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `token`  
 [in] O token de método.  
  
 `version`  
 [in] A versão do método.  
  
 `pRetVal`  
 [out] Um ponteiro para a interface retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
