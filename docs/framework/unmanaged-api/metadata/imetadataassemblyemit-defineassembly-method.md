---
title: "Método IMetaDataAssemblyEmit::DefineAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 86002eb38d72ee628dbf54d0b5691f0816e6f996
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>Método IMetaDataAssemblyEmit::DefineAssembly
Cria um `Assembly` estrutura que contém metadados para o assembly especificado e retorna o token de metadados associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
#### <a name="parameters"></a>Parâmetros  
 `pbPublicKey`  
 [in] A chave pública que identifica o Editor do assembly, ou nulo se o assembly não tem nome forte.  
  
 `cbPublicKey`  
 [in] O tamanho em bytes do `pbPublicKey`.  
  
 `uHashAlgId`  
 [in] O identificador do algoritmo de hash a ser usado para criptografar os arquivos de assembly ou nulo para especificar o algoritmo SHA-1.  
  
 `szName`  
 [in] O nome de texto legível do assembly. Esse valor não deve exceder 1024 caracteres.  
  
 `pMetaData`  
 [in] Um ponteiro para uma instância ASSEMBLYMETADATA que contém as informações de localidade, plataforma e versão do assembly.  
  
 `dwAssemblyFlags`  
 [in] Uma combinação de [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores que descrevem os recursos do assembly.  
  
 `pmda`  
 [out] Um ponteiro para o token de metadados.  
  
## <a name="remarks"></a>Comentários  
 Apenas um `Assembly` estrutura de metadados pode ser definida em um manifesto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
