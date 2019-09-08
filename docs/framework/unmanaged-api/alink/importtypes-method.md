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
ms.openlocfilehash: f19dd114925ed1fd12bcc0056411c3e3d4181215
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777087"
---
# <a name="importtypes-method"></a>Método ImportTypes
Inicia a importação de tipos de cada escopo importado por meio do [Método ImportFile](importfile-method.md).  
  
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
 ID do assembly para o qual importar.  
  
 `FileToken`  
 ID do arquivo do qual importar.  
  
 `dwScope`  
 Escopo de base zero para importar.  
  
 `phEnum`  
 Recebe o identificador do enumerador para os tipos neste escopo.  
  
 `ppImportScope`  
 Opcionalmente, recebe a interface de [interface IMetaDataImport](../metadata/imetadataimport-interface.md) .  
  
 `pdwCountOfTypes`  
 Opcionalmente, recebe a contagem de tipos no escopo indicado.  
  
## <a name="return-value"></a>Valor de retorno  
 Retornará S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>Requisitos  
 Requer ALink. h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
