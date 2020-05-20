---
title: Método ISymUnmanagedWriter::SetSymAttribute
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
ms.openlocfilehash: 39b0c065a324f2b3939467901739f995bc9abbad
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614754"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a>Método ISymUnmanagedWriter::SetSymAttribute
Define um atributo personalizado com base no seu nome. Esses atributos são mantidos no repositório de símbolos, ao contrário dos atributos personalizados de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `parent`  
 no O token de metadados para o qual o atributo está sendo definido.  
  
 `name`  
 no Um ponteiro para um `WCHAR` que contém o nome do atributo.  
  
 `cData`  
 no Um `ULONG32` que indica o tamanho da `data` matriz.  
  
 `data`  
 no O valor do atributo.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter](isymunmanagedwriter-interface.md)
