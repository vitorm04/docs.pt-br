---
title: Método IMetaDataAssemblyImport::GetAssemblyRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175961"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>Método IMetaDataAssemblyImport::GetAssemblyRefProps
Obtém o conjunto de propriedades para a referência de montagem com a assinatura de metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `mdar`  
 [em] O `mdAssemblyRef` token de metadados que representa a referência de montagem para obter as propriedades.  
  
 `ppbPublicKeyOrToken`  
 [fora] Um ponteiro para a chave pública ou o token de metadados.  
  
 `pcbPublicKeyOrToken`  
 [fora] O número de bytes na chave pública retornada ou token.  
  
 `szName`  
 [fora] O nome simples da assembléia.  
  
 `cchName`  
 [em] O tamanho, em grandes `szName`chars, de .  
  
 `pchName`  
 [fora] Um ponteiro para o número de chars largos realmente retornou em `szName`.  
  
 `pMetaData`  
 [fora] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do conjunto.  
  
 `ppbHashValue`  
 [fora] Um ponteiro para o valor de hash. Este é o hash, usando o algoritmo `PublicKey` SHA-1, da propriedade do conjunto que está sendo referenciada, a menos que a bandeira arfFullOriginator da enumeração [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) seja definida.  
  
 `pcbHashValue`  
 [fora] O número de chars largos no valor de hash devolvido.  
  
 `pdwAssemblyRefFlags`  
 [fora] Um ponteiro para bandeiras que descrevem os metadados aplicados a uma montagem. O valor das bandeiras é uma combinação de um ou mais valores [corassemblyflags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)  
  
## <a name="return-value"></a>Valor retornado  
 Este método retorna S_OK se for bem sucedido; caso contrário, ele retorna um dos códigos de erro definidos no arquivo winerror.h header.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
