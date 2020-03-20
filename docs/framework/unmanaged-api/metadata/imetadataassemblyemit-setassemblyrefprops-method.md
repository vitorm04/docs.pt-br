---
title: Método IMetaDataAssemblyEmit::SetAssemblyRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176039"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>Método IMetaDataAssemblyEmit::SetAssemblyRefProps
Modifica a estrutura `AssemblyRef` de metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `ar`  
 [em] O token de metadados `AssemblyRef` que especifica a estrutura de metadados a ser modificada.  
  
 `pbPublicKeyOrToken`  
 [em] A chave pública do editor da montagem referenciada.  
  
 `cbPublicKeyOrToken`  
 [em] O tamanho em bytes de `pbPublicKeyOrToken`.  
  
 `szName`  
 [em] O nome de texto de leitura humana da assembléia.  
  
 `pMetaData`  
 [em] Um ponteiro para uma instância ASSEMBLYMETADATA que contém as informações de versão, plataforma e local para o conjunto.  
  
 `pbHashValue`  
 [em] Um ponteiro para os dados de hash associados à montagem.  
  
 `cbHashValue`  
 [em] O tamanho em bytes de `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [em] Uma combinação bitwise dos valores [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) que especificam atributos do conjunto referenciado.  
  
## <a name="remarks"></a>Comentários  
 Para criar `AssemblyRef` uma estrutura de metadados, use o método [IMetaDataAssemblyEmit::DefineAssemblyRef.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
