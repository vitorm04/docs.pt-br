---
title: Método ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
ms.openlocfilehash: 2b5a42c89e0e3efed61b1b471c227e0df85a51aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614897"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a>Método ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
Obtém informações de pesquisa de símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cSearchInfo`  
 no Um `ULONG32` que indica o tamanho de `rgpSearchInfo` .  
  
 `pcSearchInfo`  
 fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter as informações de pesquisa.  
  
 `rgpSearchInfo`  
 fora Um ponteiro que é definido para a interface [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) retornada.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedReaderSymbolSearchInfo](isymunmanagedreadersymbolsearchinfo-interface.md)
