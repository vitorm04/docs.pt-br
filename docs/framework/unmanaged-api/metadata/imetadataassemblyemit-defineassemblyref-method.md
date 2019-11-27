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
ms.openlocfilehash: c88b7a401a19b1bd0e02edab7ef7bbee1372199e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432084"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>Método IMetaDataAssemblyEmit::DefineAssemblyRef
Cria uma estrutura de `AssemblyRef` que contém metadados para o assembly ao qual este assembly faz referência e retorna o token de metadados associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no A chave pública do Publicador do assembly referenciado. A função auxiliar [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) pode ser usada para obter o hash da chave pública a ser passada como esse parâmetro.  
  
 `cbPublicKeyOrToken`  
 no O tamanho em bytes de `pbPublicKeyOrToken`.  
  
 `szName`  
 no O nome de texto legível por humanos do assembly. Esse valor não deve exceder 1024 caracteres.  
  
 `pMetaData`  
 no Uma instância de ASSEMBLYMETADATA que contém a versão, a plataforma e as informações de localidade do assembly referenciado.  
  
 `pbHashValue`  
 no Os dados de hash associados ao assembly referenciado. Opcional.  
  
 `cbHashValue`  
 no O tamanho em bytes de `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 no Uma combinação bits de valores [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) que influencia o comportamento do mecanismo de execução.  
  
 `pmdar`  
 fora Um ponteiro para o token de metadados de `AssemblyRef` retornado.  
  
## <a name="remarks"></a>Comentários  
 Uma estrutura de metadados `AssemblyRef` deve ser definida para cada assembly referenciado por esse assembly.  
  
 Em tempo de execução, os detalhes de um assembly referenciado são passados para o resolvedor de assembly com uma indicação de que eles representam as informações "como criadas". Em seguida, o resolvedor de assembly aplica a política.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
