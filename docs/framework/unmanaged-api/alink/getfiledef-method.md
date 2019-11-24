---
title: Método GetFileDef
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 6a561205602920123176bd421ca2ef1b601166c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426056"
---
# <a name="getfiledef-method"></a>Método GetFileDef
Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID of the assembly.  
  
 `TargetFile`  
 Token of the added file as retrieved from AddFile Method or AddImport Method.  
  
 `pScope`  
 Receives the FileDef token.  
  
## <a name="return-value"></a>Valor retornado  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Requisitos  
 Requires alink.h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink2](ialink2-interface.md)
- [Interface IALink](ialink-interface.md)
- [API do ALink](index.md)
