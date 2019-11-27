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
ms.openlocfilehash: 0b7ca6f9878ed2fa2d90ea93e5101f0a66ec2d5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440214"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>Método IMetaDataAssemblyEmit::DefineFile
Cria uma estrutura de metadados `File` que contém metadados para o assembly referenciado por esse assembly e retorna o token de metadados associado.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `szName`  
 no O nome do arquivo a ser consumido.  
  
 `pbHashValue`  
 no Um ponteiro para os dados de hash associados ao assembly.  
  
 `cbHashValue`  
 no O tamanho em bytes de `pbHashValue`.  
  
 `dwFileFlags`  
 no Uma combinação de bits de `FileFlags` de valores que especifica configurações de propriedade.  
  
 `pmdf`  
 fora Um ponteiro para o token de `File` retornado.  
  
## <a name="remarks"></a>Comentários  
 Uma estrutura de metadados `File` deve ser definida para cada arquivo que faz parte desse assembly no momento em que esse assembly foi criado, excluindo o arquivo que contém os metadados.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
