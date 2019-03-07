---
title: Método SetAssemblyFile2
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 41e10855a7254da4124ac0bf9aa247b90311632b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479071"
---
# <a name="setassemblyfile2-method"></a>Método SetAssemblyFile2
Define o nome e as opções para um novo assembly. Não chame este método quando você produzir módulos não associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pszFilename`  
 Nome do arquivo de manifesto.  
  
 `pEmitter`  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface para esse arquivo.  
  
 `afFlags`  
 Opções de representado por [enumeração AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Recebe a ID exclusiva para o assembly que está sendo construído.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Consulte também
- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
