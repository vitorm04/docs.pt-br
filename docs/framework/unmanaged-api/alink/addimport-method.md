---
title: Método AddImport
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aed70a78e2513f4d63fbf8ca8868f26efbac9ae8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787657"
---
# <a name="addimport-method"></a>Método AddImport
Adiciona importações ao assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID exclusiva do assembly a ser aumentada.  
  
 `ImportToken`  
 ID exclusiva, recuperada do [Método ImportFile](importfile-method.md), do arquivo a ser importado.  
  
 `dwFlags`  
 Sinalizadores de `ffContainsNoMetaData` FileDef com+, como `ffWriteable`e. `dwFlags`é passado para o [método definofile](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Ponteiro para token que recebe a ID do arquivo resultante.  
  
## <a name="return-value"></a>Valor de retorno  
 Retornará S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>Requisitos  
 Requer ALink. h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
