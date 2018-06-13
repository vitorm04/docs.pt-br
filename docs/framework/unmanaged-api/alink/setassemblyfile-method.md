---
title: Método SetAssemblyFile
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e557cc0da7bc684843ae3969242ffb84d811c44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405340"
---
# <a name="setassemblyfile-method"></a>Método SetAssemblyFile
Atribui o nome do assembly a ser criado. Não para uso durante a produção de módulos não associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszFilename`  
 Nome totalmente qualificado do arquivo de manifesto.  
  
 `pEmitter`  
 Ponteiro para [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.  
  
 `afFlags`  
 Sinalizadores conforme definido em [enumeração AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Ponteiro para a ID do assembly resultante.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna S_OK se o método for bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
