---
title: Método ISymENCUnmanagedMethod::GetLineFromOffset
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 94a571a4bc01b805387aebe5a6e23bad0b735313
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448645"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>Método ISymENCUnmanagedMethod::GetLineFromOffset
Gets the line information associated with an offset. If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwOffset`  
 [in] A `ULONG32` that contains the offset.  
  
 `pline`  
 [out] A pointer to a `ULONG32` that receives the line.  
  
 `pcolumn`  
 [out] A pointer to a `ULONG32` that receives the column.  
  
 `pendLine`  
 [out] A pointer to a `ULONG32` that receives the end line.  
  
 `pendColumn`  
 [out] A pointer to a `ULONG32` that receives the end column.  
  
 `pdwStartOffset`  
 [out] A pointer to a `ULONG32` that receives the associated sequence point.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Requisitos  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymENCUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
