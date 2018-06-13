---
title: Método IMetaDataImport::GetPropertyProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7312cbd31a04365801b0380d5914966f36679560
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449449"
---
# <a name="imetadataimportgetpropertyprops-method"></a>Método IMetaDataImport::GetPropertyProps
Obtém os metadados da propriedade representada pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `prop`  
 [in] Um token que representa a propriedade para retornar metadados.  
  
 `pClass`  
 [out] Um ponteiro para o token de TypeDef que representa o tipo que implementa a propriedade.  
  
 `szProperty`  
 [out] Um buffer para armazenar o nome da propriedade.  
  
 `cchProperty`  
 [in] O tamanho em caracteres largos de `szProperty`.  
  
 `pchProperty`  
 [out] O número de caracteres largos retornados em `szProperty`.  
  
 `pdwPropFlags`  
 [out] Um ponteiro para os sinalizadores de atributo aplicado à propriedade. Esse valor é um bitmask do [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeração.  
  
 `ppvSig`  
 [out] Um ponteiro para a assinatura de metadados da propriedade.  
  
 `pbSig`  
 [out] O número de bytes retornados em `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] Um sinalizador que especifica o tipo de constante que é o valor padrão da propriedade. Esse valor é da enumeração CorElementType.  
  
 `ppDefaultValue`  
 [out] Um ponteiro para os bytes que armazena o valor padrão para essa propriedade.  
  
 `pcchDefaultValue`  
 [out] O tamanho em caracteres largos de `ppDefaultValue`, se `pdwCPlusTypeFlag` é ELEMENT_TYPE_STRING; caso contrário, esse valor não é relevante. Nesse caso, o comprimento de `ppDefaultValue` é inferido do tipo especificado pelo `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] Um ponteiro para o token MethodDef que representa o método de acessador set da propriedade.  
  
 `pmdGetter`  
 [out] Um ponteiro para o token MethodDef que representa o método de acessador get da propriedade.  
  
 `rmdOtherMethod`  
 [out] Uma matriz de MethodDef tokens que representam os outros métodos associados à propriedade.  
  
 `cMax`  
 [in] O tamanho máximo da `rmdOtherMethod` matriz. Se você não fornecer uma matriz grande o suficiente para manter todos os métodos, eles serão ignorados sem aviso.  
  
 `pcOtherMethod`  
 [out] O número de tokens de MethodDef retornados em `rmdOtherMethod`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
