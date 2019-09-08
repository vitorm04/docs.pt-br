---
title: Método ExportNestedType
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 570e48788a11045882ef546bf6bc22315c2a02b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777269"
---
# <a name="exportnestedtype-method"></a>Método ExportNestedType
Especifica os tipos aninhados como exportáveis. O [método ExportType](exporttype-method.md) também pode exportar tipos aninhados, mas esse método é mais rápido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly do qual exportar.  
  
 `FileToken`  
 Token de arquivo ou assembly de arquivo que define o tipo a ser tornado exportável.  
  
 `TypeToken`  
 Tipo de token do tipo a ser tornado exportável.  
  
 `ParentType`  
 Token do tipo pai.  
  
 `pszTypename`  
 Nome de tipo totalmente qualificado para exportar.  
  
 `dwFlags`  
 `ComType`sinalizadores como `tdPublic` ou `tdNested`. Esse valor pode ser passado para o [método DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Recebe o token para o tipo exportado.  
  
## <a name="return-value"></a>Valor de retorno  
 Retornará S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>Requisitos  
 Requer ALink. h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
