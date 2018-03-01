---
title: "Método IMetaDataAssemblyEmit::DefineAssemblyRef"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 123bd37d189477eade72e3b0e74f923fecce57a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>Parâmetros  
 `pbPublicKeyOrToken`  
 [in] A chave pública do publicador do assembly referenciado. A função auxiliar [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) pode ser usado para obter o hash da chave pública para passar como esse parâmetro.  
  
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
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
