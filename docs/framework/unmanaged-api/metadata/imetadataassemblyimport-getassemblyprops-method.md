---
title: Método IMetaDataAssemblyImport::GetAssemblyProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177782"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>Método IMetaDataAssemblyImport::GetAssemblyProps
Obtém o conjunto de propriedades para o conjunto com a assinatura de metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `mda`  
 [in]. O `mdAssembly` token de metadados que representa o conjunto para o qual obter as propriedades.  
  
 `ppbPublicKey`  
 [fora] Um ponteiro para a chave pública ou o token de metadados.  
  
 `pcbPublicKey`  
 [fora] O número de bytes na chave pública devolvida.  
  
 `pulHashAlgId`  
 [fora] Um ponteiro para o algoritmo usado para hash os arquivos na montagem.  
  
 `szName`  
 [fora] O nome simples da assembléia.  
  
 `cchName`  
 [em] O tamanho, em grandes `szName`chars, de .  
  
 `pchName`  
 [fora] O número de chars largos realmente retornou em `szName`.  
  
 `pMetaData`  
 [fora] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do conjunto.  
  
 `pdwAssemblyFlags`  
 [fora] Sinalizadores que descrevem os metadados aplicados a uma montagem. Este valor é uma combinação de um ou mais valores [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
