---
title: Método IMetaDataAssemblyImport::EnumFiles
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2ab06419491093a2de41d2ef25d16c01c03ebaf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905327"
---
# <a name="imetadataassemblyimportenumfiles-method"></a>Método IMetaDataAssemblyImport::EnumFiles
Enumera os arquivos referenciados no manifesto do assembly atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [no, out] Um ponteiro para o enumerador. Isso deve ser um valor nulo para a primeira chamada desse método.  
  
 `rFiles`  
 [out] A matriz usada para armazenar o `mdFile` tokens de metadados.  
  
 `cMax`  
 [in] O número máximo de `mdFile` tokens que podem ser colocadas em `rFiles`.  
  
 `pcTokens`  
 [out] O número de `mdFile` tokens realmente colocados nos `rFiles`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumFiles` retornado com êxito.|  
|`S_FALSE`|Não há nenhum token para enumerar. Nesse caso, `pcTokens` é definido como zero.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
