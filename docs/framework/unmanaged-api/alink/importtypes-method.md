---
title: Método ImportTypes
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9876e3ba5ea67442714c2d00b1901c25e54494f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741629"
---
# <a name="importtypes-method"></a>Método ImportTypes
Inicia a importação dos tipos de cada escopo importado por meio [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly para importar.  
  
 `FileToken`  
 ID do arquivo de origem.  
  
 `dwScope`  
 Escopo baseado em zero para importar.  
  
 `phEnum`  
 Recebe o identificador de enumerador para os tipos neste escopo.  
  
 `ppImportScope`  
 Opcionalmente, recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.  
  
 `pdwCountOfTypes`  
 Opcionalmente, receber a contagem de tipos no escopo indicado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
