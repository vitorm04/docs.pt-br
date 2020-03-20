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
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179410"
---
# <a name="exportnestedtype-method"></a>Método ExportNestedType
Especifica tipos aninhados como exportáveis. O [Método ExportarTipo](exporttype-method.md) também pode exportar tipos aninhados, mas este método é mais rápido.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `AssemblyID`  
 ID de montagem para exportação.  
  
 `FileToken`  
 Token de arquivo ou montagem de arquivo que define o tipo a ser exportável.  
  
 `TypeToken`  
 Digite o tipo de tipo a ser exportável.  
  
 `ParentType`  
 Símbolo do tipo pai.  
  
 `pszTypename`  
 Nome de tipo totalmente qualificado para exportar.  
  
 `dwFlags`  
 `ComType`bandeiras `tdPublic` como `tdNested`ou . Esse valor pode ser passado para [o método DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Recebe token para o tipo exportado.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método for bem sucedido.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h  
  
## <a name="see-also"></a>Confira também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
