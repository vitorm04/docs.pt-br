---
title: Método ISymUnmanagedReader2::GetMethodsInDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28b240159c36b03b2c476f56f7e6ad7b33f20649
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142332"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a>Método ISymUnmanagedReader2::GetMethodsInDocument
Obtém todos os métodos que tem informações de linha no documento fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `document`  
 [in] Um ponteiro para o documento.  
  
 `cMethod`  
 [in] Um `ULONG32` que indica o tamanho do `pRetVal` matriz.  
  
 `pcMethod`  
 [out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os métodos.  
  
 `pRetVal`  
 [out] Um ponteiro para o buffer que recebe os métodos.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedReader2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
