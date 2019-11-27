---
title: Método ISymUnmanagedReader2::GetSymAttributePreRemap
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 4009f8988c90ed090c0cc3d86164af347055722f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446425"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>Método ISymUnmanagedReader2::GetSymAttributePreRemap
Obtém um atributo personalizado com base no seu nome. Ao contrário dos atributos personalizados de metadados, esses atributos são mantidos no repositório de símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `parent`  
 no O token de metadados do pai.  
  
 `name`  
 no Um ponteiro para um `WCHAR` que contém o nome.  
  
 `cBuffer`  
 no Um `ULONG32` que indica o tamanho da matriz de `buffer`.  
  
 `pcBuffer`  
 fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os bytes do atributo.  
  
 `buffer`  
 fora Um ponteiro para o buffer que recebe os bytes de atributo.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedReader2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
