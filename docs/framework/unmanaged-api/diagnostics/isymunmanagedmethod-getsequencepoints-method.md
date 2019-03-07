---
title: Método ISymUnmanagedMethod::GetSequencePoints
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad9e552d31944523222798fe7dba2201461b1243
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487237"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>Método ISymUnmanagedMethod::GetSequencePoints
Obtém todos os pontos de sequência dentro desse método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cPoints`  
 [in] Um `ULONG32` que recebe o tamanho do `offsets`, `documents`, `lines`, `columns`, `endLines`, e `endColumns` matrizes.  
  
 `pcPoints`  
 [out] Um ponteiro para um `ULONG32` que recebe o comprimento do buffer necessário para conter os pontos de sequência.  
  
 `offsets`  
 [in] Uma matriz na qual armazenar o Microsoft intermediate language (MSIL) deslocamentos do início do método para os pontos de sequência.  
  
 `documents`  
 [in] Uma matriz na qual armazenar os documentos em que os pontos de sequência estão localizados.  
  
 `lines`  
 [in] Uma matriz na qual deseja armazenar as linhas nos documentos em que os pontos de sequência estão localizados.  
  
 `columns`  
 [in] Uma matriz na qual deseja armazenar as colunas nos documentos em que os pontos de sequência estão localizados.  
  
 `endLines`  
 [in] A matriz de linhas nos documentos em que a sequência de pontos termina.  
  
 `endColumns`  
 [in] A matriz de colunas nos documentos em que a sequência de pontos termina.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
