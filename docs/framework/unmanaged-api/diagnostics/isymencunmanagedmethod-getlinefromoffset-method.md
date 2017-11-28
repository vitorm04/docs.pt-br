---
title: "Método ISymENCUnmanagedMethod::GetLineFromOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetLineFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f18357b3a58a5409da93d4d2491997e9ca1cc70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>Método ISymENCUnmanagedMethod::GetLineFromOffset
Obtém as informações de linha associadas com um deslocamento. Se o parâmetro de deslocamento (`dwOffset`) não é um ponto de sequência, esse método obtém as informações de linha associadas com o deslocamento anterior.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwOffset`  
 [in] Um `ULONG32` que contém o deslocamento.  
  
 `pline`  
 [out] Um ponteiro para um `ULONG32` que recebe a linha.  
  
 `pcolumn`  
 [out] Um ponteiro para um `ULONG32` que recebe a coluna.  
  
 `pendLine`  
 [out] Um ponteiro para um `ULONG32` que recebe a fim de linha.  
  
 `pendColumn`  
 [out] Um ponteiro para um `ULONG32` que recebe a coluna final.  
  
 `pdwStartOffset`  
 [out] Um ponteiro para um `ULONG32` que recebe o ponto de sequência associado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymENCUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
