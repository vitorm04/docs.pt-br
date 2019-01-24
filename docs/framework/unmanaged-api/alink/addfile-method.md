---
title: Método1 AddFile
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84b68638ed0f7a86156cf7e5fcc98d3c02cba18a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662602"
---
# <a name="addfile-method1"></a>Método1 AddFile
Adiciona arquivos ao assembly. Também pode ser usado para criar os módulos não associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID exclusiva do assembly a ser aumentado.  
  
 `pszFilename`  
 Nome totalmente qualificado do arquivo a ser adicionado.  
  
 `dwFlags`  
 Como sinalizadores de COM+ FileDef `ffContainsNoMetaData` e `ffWriteable`. `dwFlags` é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface a ser usado para emitir metadados, se necessário.  
  
 `pFileToken`  
 Ponteiro para onde a ID exclusiva do arquivo adicionado será armazenada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Consulte também
- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
