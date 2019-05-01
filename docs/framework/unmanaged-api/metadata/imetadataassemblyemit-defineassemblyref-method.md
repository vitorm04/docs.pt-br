---
title: Método IMetaDataAssemblyEmit::DefineAssemblyRef
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e480c408c10eb9e135f260426750f7747e5d8ce5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044766"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>Método IMetaDataAssemblyEmit::DefineAssemblyRef
Cria um `AssemblyRef` estrutura que contém metadados para o assembly que faz referência a esse assembly e retorna o token de metadados associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pbPublicKeyOrToken`  
 [in] A chave pública do Editor do assembly referenciado. A função auxiliar [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) pode ser usado para obter o hash da chave pública para passar como este parâmetro.  
  
 `cbPublicKeyOrToken`  
 [in] O tamanho em bytes do `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] O nome de texto legível do assembly. Esse valor não deve exceder 1024 caracteres.  
  
 `pMetaData`  
 [in] Uma instância ASSEMBLYMETADATA que contém as informações de versão, a plataforma e a localidade do assembly referenciado.  
  
 `pbHashValue`  
 [in] O hash de dados associados ao assembly referenciado. Opcional.  
  
 `cbHashValue`  
 [in] O tamanho em bytes do `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Uma combinação bit a bit de [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores que influenciam o comportamento do mecanismo de execução.  
  
 `pmdar`  
 [out] Um ponteiro para retornado `AssemblyRef` token de metadados.  
  
## <a name="remarks"></a>Comentários  
 Um `AssemblyRef` estrutura de metadados deve ser definida para cada assembly que faz referência a esse assembly.  
  
 Em tempo de execução, os detalhes de um assembly referenciado são passados para o resolvedor de assembly com uma indicação de que eles representam as informações "no estado criado". O resolvedor de assembly, em seguida, aplica a política.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
