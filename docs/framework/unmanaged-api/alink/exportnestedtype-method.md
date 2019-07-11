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
ms.openlocfilehash: 7dfaedad48291ac09f6959bc7b314ae0d9da76e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742050"
---
# <a name="exportnestedtype-method"></a>Método ExportNestedType
Especifica os tipos aninhados como exportável. O [método ExportType](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) também pode tipos aninhado de exportação, mas esse método é mais rápido.  
  
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
 ID do assembly para exportação.  
  
 `FileToken`  
 Token de arquivo ou Assembly de arquivo que define o tipo a ser feita exportável.  
  
 `TypeToken`  
 Tipo de token do tipo a ser feita exportável.  
  
 `ParentType`  
 Token do tipo pai.  
  
 `pszTypename`  
 Nome de tipo totalmente qualificado para exportar.  
  
 `dwFlags`  
 `ComType` sinalizadores como `tdPublic` ou `tdNested`. Esse valor pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Recebe o token para o tipo exportado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
