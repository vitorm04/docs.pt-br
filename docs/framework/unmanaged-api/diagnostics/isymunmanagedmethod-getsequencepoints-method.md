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
ms.openlocfilehash: 451cfecde7e14fad9d3fed3367112e1fb59796e5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615138"
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
 no Um `ULONG32` que recebe o tamanho das `offsets` `documents` matrizes,, `lines` ,, `columns` `endLines` e `endColumns` .  
  
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
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedMethod](isymunmanagedmethod-interface.md)
