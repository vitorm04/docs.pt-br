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
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437132"
---
# <a name="imetadataimportgetparamprops-method"></a>Método IMetaDataImport::GetParamProps
Obtém valores de metadados para o parâmetro referenciado pelo token ParamDef especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no Um token ParamDef que representa o parâmetro para o qual retornar metadados.  
  
 `pmd`  
 fora Um ponteiro para um token MethodDef que representa o método que usa o parâmetro.  
  
 `pulSequence`  
 fora A posição ordinal do parâmetro na lista de argumentos do método.  
  
 `szName`  
 fora Um buffer para armazenar o nome do parâmetro.  
  
 `cchName`  
 no O tamanho solicitado em caracteres largos de `szName`.  
  
 `pchName`  
 fora O tamanho retornado em caracteres largos de `szName`.  
  
 `pdwAttr`  
 fora Um ponteiro para qualquer sinalizador de atributo associado ao parâmetro. Este é um bitmask de valores de `CorParamAttr`.  
  
 `pdwCPlusTypeFlag`  
 fora Um ponteiro para um sinalizador que especifica que o parâmetro é um <xref:System.ValueType>.  
  
 `ppValue`  
 fora Um ponteiro para uma cadeia de caracteres constante retornada pelo parâmetro.  
  
 `pcchValue`  
 fora O tamanho de `ppValue` em caracteres largos ou zero se `ppValue` não mantiver uma cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários

Os valores de sequência em `pulSequence` começam com 1 para parâmetros. Um valor de retorno tem um número de sequência de 0.

## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
