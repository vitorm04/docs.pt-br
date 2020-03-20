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
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175324"
---
# <a name="imetadataimportgetpropertyprops-method"></a>Método IMetaDataImport::GetPropertyProps
Obtém os metadados da propriedade representada pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>parâmetros  
 `prop`  
 [em] Um token que representa a propriedade para retornar metadados.  
  
 `pClass`  
 [fora] Um ponteiro para o token TypeDef que representa o tipo que implementa a propriedade.  
  
 `szProperty`  
 [fora] Um tampão para manter o nome da propriedade.  
  
 `cchProperty`  
 [em] O tamanho em `szProperty`caracteres largos de .  
  
 `pchProperty`  
 [fora] O número de personagens `szProperty`amplos retornou em .  
  
 `pdwPropFlags`  
 [fora] Um ponteiro para quaisquer bandeiras de atributo aplicadas à propriedade. Este valor é uma máscara de bitda da enumeração [CorPropertyAttr.](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)  
  
 `ppvSig`  
 [fora] Um ponteiro para a assinatura de metadados da propriedade.  
  
 `pbSig`  
 [fora] O número de bytes `ppvSig`retornou em .  
  
 `pdwCPlusTypeFlag`  
 [fora] Um sinalizador especificando o tipo de constante que é o valor padrão da propriedade. Este valor é da enumeração CorElementType.  
  
 `ppDefaultValue`  
 [fora] Um ponteiro para os bytes que armazenam o valor padrão para esta propriedade.  
  
 `pcchDefaultValue`  
 [fora] O tamanho em `ppDefaultValue`caracteres `pdwCPlusTypeFlag` largos de , se é ELEMENT_TYPE_STRING; caso contrário, esse valor não é relevante. Nesse caso, o `ppDefaultValue` comprimento do é inferido do `pdwCPlusTypeFlag`tipo especificado por .  
  
 `pmdSetter`  
 [fora] Um ponteiro para o token MethodDef que representa o método do acessório definido para a propriedade.  
  
 `pmdGetter`  
 [fora] Um ponteiro para o token MethodDef que representa o método get accessor for the property.  
  
 `rmdOtherMethod`  
 [fora] Uma matriz de tokens MethodDef que representam outros métodos associados à propriedade.  
  
 `cMax`  
 [em] O tamanho máximo `rmdOtherMethod` da matriz. Se você não fornecer uma matriz grande o suficiente para manter todos os métodos, eles são ignorados sem aviso.  
  
 `pcOtherMethod`  
 [fora] O número de tokens MethodDef retornado em `rmdOtherMethod`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
