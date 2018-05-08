---
title: Método IMetaDataAssemblyEmit::SetAssemblyProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f8132296035e9ddcdcad76d93ed05358beb0b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>Método IMetaDataAssemblyEmit::SetAssemblyProps
Modifica especificado `Assembly` estrutura de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pma`  
 [in] O token de metadados que especifica o `Assembly` estrutura de metadados a ser modificado.  
  
 `pbPublicKey`  
 [in] Um ponteiro para a chave pública do publicador do assembly.  
  
 `cbPublicKey`  
 [in] O tamanho em bytes do `pbPublicKey`.  
  
 `ulHashAlgId`  
 [in] O identificador para o algoritmo de hash usado para os arquivos de assembly de hash.  
  
 `szName`  
 [in] O nome de texto legível do assembly.  
  
 `pMetaData`  
 [in] Um ponteiro para o ASSEMBLYMETADATA que contém informações de localidade, plataforma e versão do assembly.  
  
 `dwAssemblyFlags`  
 [in] Uma combinação bit a bit de [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) valores que especificam vários atributos do assembly.  
  
## <a name="remarks"></a>Comentários  
 Para criar um `Assembly` estrutura de metadados, use o [: Defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
