---
title: Método IMetaDataAssemblyEmit::DefineFile
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: cabd6a47e5d6fc2a4cea87b16d349d9c778b3507
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176052"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>Método IMetaDataAssemblyEmit::DefineFile
Cria `File` uma estrutura de metadados contendo metadados para montagem referenciada por este conjunto e retorna o token de metadados associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `szName`  
 [em] O nome do arquivo a ser consumido.  
  
 `pbHashValue`  
 [em] Um ponteiro para os dados de hash associados à montagem.  
  
 `cbHashValue`  
 [em] O tamanho em bytes de `pbHashValue`.  
  
 `dwFileFlags`  
 [em] Uma combinação bitwise de `FileFlags` valores que especificam configurações de propriedade.  
  
 `pmdf`  
 [fora] Um ponteiro para `File` o token devolvido.  
  
## <a name="remarks"></a>Comentários  
 Uma `File` estrutura de metadados deve ser definida para cada arquivo que fazia parte desta montagem no momento em que este conjunto foi construído, excluindo o arquivo que contém os metadados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
