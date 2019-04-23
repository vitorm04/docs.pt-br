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
ms.openlocfilehash: bbe8a43f44d59249abc713c95fce31f1fb9a5993
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148662"
---
# <a name="addimport-method"></a>Método AddImport
Adiciona importações ao assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID exclusiva do assembly a ser aumentado.  
  
 `ImportToken`  
 ID exclusiva, recuperados do [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), do arquivo a ser importado.  
  
 `dwFlags`  
 Como sinalizadores de COM+ FileDef `ffContainsNoMetaData` e `ffWriteable`. `dwFlags` é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Ponteiro para o token que recebe a ID para o arquivo resultante.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
