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
ms.openlocfilehash: 75d477af7395a9b7d3328b2a5787f810733f3749
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448881"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>Método ISymUnmanagedMethod::GetSequencePoints
Obtém todos os pontos de sequência dentro deste método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no Um `ULONG32` que recebe o tamanho das matrizes `offsets`, `documents`, `lines`, `columns`, `endLines`e `endColumns`.  
  
 `pcPoints`  
 fora Um ponteiro para um `ULONG32` que recebe o comprimento do buffer necessário para conter os pontos de sequência.  
  
 `offsets`  
 no Uma matriz na qual armazenar os deslocamentos da MSIL (Microsoft Intermediate Language) do início do método para os pontos de sequência.  
  
 `documents`  
 no Uma matriz na qual armazenar os documentos nos quais os pontos de sequência estão localizados.  
  
 `lines`  
 no Uma matriz na qual armazenar as linhas nos documentos nos quais os pontos de sequência estão localizados.  
  
 `columns`  
 no Uma matriz na qual armazenar as colunas nos documentos nos quais os pontos de sequência estão localizados.  
  
 `endLines`  
 no A matriz de linhas nos documentos em que os pontos de sequência terminam.  
  
 `endColumns`  
 no A matriz de colunas nos documentos em que os pontos de sequência terminam.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
