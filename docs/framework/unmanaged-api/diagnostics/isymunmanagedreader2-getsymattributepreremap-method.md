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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 543a8015e944333942b619060059273577902a74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110286"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>Método ISymUnmanagedReader2::GetSymAttributePreRemap
Obtém um atributo personalizado com base em seu nome. Ao contrário de atributos personalizados de metadados, esses atributos são mantidos no repositório de símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 [in] O token de metadados do pai.  
  
 `name`  
 [in] Um ponteiro para um `WCHAR` que contém o nome.  
  
 `cBuffer`  
 [in] Um `ULONG32` que indica o tamanho do `buffer` matriz.  
  
 `pcBuffer`  
 [out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os bytes de atributo.  
  
 `buffer`  
 [out] Um ponteiro para o buffer que recebe os bytes de atributo.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedReader2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
