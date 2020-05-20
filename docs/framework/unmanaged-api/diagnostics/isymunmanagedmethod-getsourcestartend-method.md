---
title: Método ISymUnmanagedMethod::GetSourceStartEnd
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: 25e797fdf563a01ab727f16e7173eec2552eeb27
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614416"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a>Método ISymUnmanagedMethod::GetSourceStartEnd
Obtém as posições do documento inicial e final da origem deste método. A primeira posição da matriz é o início e a segunda posição da matriz é o final.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `docs`  
 no Os documentos de origem inicial e final.  
  
 `lines`  
 no As linhas inicial e final nos documentos de origem correspondentes.  
  
 `columns`  
 no As colunas inicial e final nos documentos de origem correspondentes.  
  
 `pRetVal`  
 [fora] `true` Se as posições foram definidas; caso contrário, `false` .  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Veja também

- [Interface ISymUnmanagedMethod](isymunmanagedmethod-interface.md)
