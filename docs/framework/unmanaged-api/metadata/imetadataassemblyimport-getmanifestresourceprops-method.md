---
title: Método IMetaDataAssemblyImport::GetManifestResourceProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177654"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>Método IMetaDataAssemblyImport::GetManifestResourceProps
Obtém o conjunto de propriedades do recurso manifesto com a assinatura de metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `mdmr`  
 [em] Um `mdManifestResource` token que representa o recurso para obter as propriedades.  
  
 `szName`  
 [fora] O nome do recurso.  
  
 `cchName`  
 [em] O tamanho, em grandes `szName`chars, de .  
  
 `pchName`  
 [fora] Um ponteiro para o número de chars largos realmente retornou em `szName`.  
  
 `ptkImplementation`  
 [fora] Um ponteiro `mdFile` para um `mdAssemblyRef` token ou um token que representa o arquivo ou conjunto, respectivamente, que contém o recurso.  
  
 `pdwOffset`  
 [fora] Um ponteiro para um valor que especifica o deslocamento para o início do recurso dentro do arquivo.  
  
 `pdwResourceFlags`  
 [fora] Um ponteiro para sinalizadores que descrevem os metadados aplicados a um recurso. O valor dos sinalizadores é uma combinação de um ou mais valores [do CorManifestResourceFlags.](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
