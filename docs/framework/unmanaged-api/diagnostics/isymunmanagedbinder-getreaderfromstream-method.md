---
title: Método ISymUnmanagedBinder::GetReaderFromStream
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c5d3d1b868849d17b2068eecfcfeea0f1e598f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a>Método ISymUnmanagedBinder::GetReaderFromStream
Dado uma interface de metadados e um fluxo que contém o repositório de símbolos, retorna o correto [ISymUnmanagedReader](isymunmanagedreader-interface.md) símbolos de estrutura que lerá a depuração do armazenamento de símbolo dado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `importer`  
 [in] Um ponteiro para a interface de importação de metadados.  
  
 `pstream`  
 [in] Um ponteiro para o fluxo que contém o repositório de símbolos.  
  
 `pRetVal`  
 [out] Um ponteiro que está definido para retornado [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
