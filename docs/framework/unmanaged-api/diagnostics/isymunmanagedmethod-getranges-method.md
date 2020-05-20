---
title: Método ISymUnmanagedMethod::GetRanges
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
ms.openlocfilehash: cd5d1f2d59d3e55ba454f23d2e5dd4b1316c0df4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615170"
---
# <a name="isymunmanagedmethodgetranges-method"></a>Método ISymUnmanagedMethod::GetRanges
Dada uma posição em um documento, retorna uma matriz de pares de deslocamento inicial e final que correspondem aos intervalos da MSIL (Microsoft Intermediate Language) que a posição aborda nesse método. A matriz é uma matriz de inteiros e tem o formato [início, fim, início, fim]. O número de pares de intervalo é o comprimento da matriz dividida por 2.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `document`  
 no O documento para o qual o deslocamento é solicitado.  
  
 `line`  
 no A linha do documento correspondente aos intervalos.  
  
 `column`  
 no A coluna de documento correspondente aos intervalos.  
  
 `cRanges`  
 no O tamanho da `ranges` matriz.  
  
 `pcRanges`  
 fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os intervalos.  
  
 `ranges`  
 fora Um ponteiro para o buffer que recebe os intervalos.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedMethod](isymunmanagedmethod-interface.md)
