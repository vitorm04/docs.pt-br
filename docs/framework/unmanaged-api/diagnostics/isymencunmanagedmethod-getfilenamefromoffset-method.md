---
title: Método ISymENCUnmanagedMethod::GetFileNameFromOffset
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 74002ce9c76eebaa3ea5860b09cd3e7c9a884f8d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448661"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a>Método ISymENCUnmanagedMethod::GetFileNameFromOffset
Obtém o nome do arquivo da linha associada a um deslocamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwOffset`  
 no Um `ULONG32` que contém o deslocamento.  
  
 `cchName`  
 no Um `ULONG32` que indica o tamanho do buffer de `szName`.  
  
 `pcchName`  
 fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter os nomes de arquivo.  
  
 `szName`  
 fora O buffer que contém os nomes de arquivo.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymENCUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
