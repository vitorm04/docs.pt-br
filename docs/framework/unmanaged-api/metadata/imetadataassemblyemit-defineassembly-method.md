---
title: Método IMetaDataAssemblyEmit::DefineAssembly
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177895"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>Método IMetaDataAssemblyEmit::DefineAssembly
Cria `Assembly` uma estrutura contendo metadados para o conjunto especificado e retorna o token de metadados associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pbPublicKey`  
 [em] A chave pública que identifica o editor da montagem, ou NULL se a montagem não for fortemente nomeada.  
  
 `cbPublicKey`  
 [em] O tamanho em bytes de `pbPublicKey`.  
  
 `uHashAlgId`  
 [em] O identificador do algoritmo de hashing para usar para criptografar os arquivos no conjunto, ou NULL para especificar o algoritmo SHA-1.  
  
 `szName`  
 [em] O nome de texto de leitura humana da assembléia. Este valor não deve exceder 1024 caracteres.  
  
 `pMetaData`  
 [em] Um ponteiro para uma instância ASSEMBLYMETADATA que contém as informações de versão, plataforma e local para o conjunto.  
  
 `dwAssemblyFlags`  
 [em] Uma combinação de valores [corassemblyflags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) que descrevem características do conjunto.  
  
 `pmda`  
 [fora] Um ponteiro para o token de metadados.  
  
## <a name="remarks"></a>Comentários  
 Apenas `Assembly` uma estrutura de metadados pode ser definida dentro de um manifesto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
