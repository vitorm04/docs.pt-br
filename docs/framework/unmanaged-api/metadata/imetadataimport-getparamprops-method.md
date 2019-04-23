---
title: Método IMetaDataImport::GetParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05ac8efed8c0a905d2cfad433348a99fe578eeae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153173"
---
# <a name="imetadataimportgetparamprops-method"></a>Método IMetaDataImport::GetParamProps
Obtém os valores de metadados para o parâmetro referenciado pelo ParamDef especificado token.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tk`  
 [in] Um token de ParamDef que representa o parâmetro para retornar metadados.  
  
 `pmd`  
 [out] Um ponteiro para um token MethodDef que representa o método que utiliza o parâmetro.  
  
 `pulSequence`  
 [out] A posição ordinal do parâmetro na lista de argumentos de método.  
  
 `szName`  
 [out] Um buffer para armazenar o nome do parâmetro.  
  
 `cchName`  
 [in] O tamanho solicitado em caracteres largos da `szName`.  
  
 `pchName`  
 [out] O tamanho retornado em caracteres largos da `szName`.  
  
 `pdwAttr`  
 [out] Um ponteiro para os sinalizadores de atributo associado ao parâmetro. Esse é um bitmask de `CorParamAttr` valores.  
  
 `pdwCPlusTypeFlag`  
 [out] Um ponteiro para um sinalizador que especifica que o parâmetro é um <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Um ponteiro para uma cadeia de caracteres constante retornado pelo parâmetro.  
  
 `pcchValue`  
 [out] O tamanho de `ppValue` em caracteres largos ou zero se `ppValue` não mantém uma cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários

Os valores de sequência no `pulSequence` começam com 1 para parâmetros. Um valor de retorno tem um número de sequência igual a 0.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
