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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6667812ab7f9acff2a66e458f68d77a0d670bc2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>Método IMetaDataAssemblyEmit::SetAssemblyRefProps
Modifica especificado `AssemblyRef` estrutura de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
#### <a name="parameters"></a>Parâmetros  
 `ar`  
 [in] O token de metadados que especifica o `AssemblyRef` estrutura de metadados a ser modificado.  
  
 `pbPublicKeyOrToken`  
 [in] A chave pública do publicador do assembly referenciado.  
  
 `cbPublicKeyOrToken`  
 [in] O tamanho em bytes do `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] O nome de texto legível do assembly.  
  
 `pMetaData`  
 [in] Um ponteiro para uma instância ASSEMBLYMETADATA que contém as informações de localidade, plataforma e versão do assembly.  
  
 `pbHashValue`  
 [in] Um ponteiro para o hash de dados associados ao assembly.  
  
 `cbHashValue`  
 [in] O tamanho em bytes do `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Uma combinação bit a bit de [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) valores que especificam os atributos do assembly referenciado.  
  
## <a name="remarks"></a>Comentários  
 Para criar um `AssemblyRef` estrutura de metadados, use o [: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
