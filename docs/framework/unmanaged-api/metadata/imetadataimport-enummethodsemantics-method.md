---
title: Método IMetaDataImport::EnumMethodSemantics
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175454"
---
# <a name="imetadataimportenummethodsemantics-method"></a>Método IMetaDataImport::EnumMethodSemantics
Enumera as propriedades e os eventos de alteração de propriedade aos quais o método especificado está relacionado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `phEnum`  
 [dentro, fora] Um ponteiro para o enumerador. Isto deve ser NULO para a primeira chamada deste método.  
  
 `mb`  
 [em] Um token MethodDef que limita o escopo da enumeração.  
  
 `rEventProp`  
 [fora] A matriz usada para armazenar os eventos ou propriedades.  
  
 `cMax`  
 [em] O tamanho máximo `rEventProp` da matriz.  
  
 `pcEventProp`  
 [fora] O número de eventos ou `rEventProp`propriedades retornadas em .  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`retornou com sucesso.|  
|`S_FALSE`|Não há eventos ou propriedades para enumerar. Nesse caso, `pcEventProp` é zero.|  
  
## <a name="remarks"></a>Comentários  
 Muitos tipos de tempo de `On`execução de idiomas comuns definem eventos de *propriedade* `Changed` e métodos de *propriedade* `Changed` relacionados às suas propriedades. Por exemplo, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> o tipo <xref:System.Windows.Forms.Control.Font%2A> define <xref:System.Windows.Forms.Control.FontChanged> uma propriedade, <xref:System.Windows.Forms.Control.OnFontChanged%2A> um evento e um método. O método de <xref:System.Windows.Forms.Control.Font%2A> acessório <xref:System.Windows.Forms.Control.OnFontChanged%2A> definido do método de <xref:System.Windows.Forms.Control.FontChanged> chamadas de propriedade, que por sua vez levanta o evento. Você `EnumMethodSemantics` ligaria usando o <xref:System.Windows.Forms.Control.OnFontChanged%2A> MethodDef para <xref:System.Windows.Forms.Control.Font%2A> obter referências à propriedade e ao <xref:System.Windows.Forms.Control.FontChanged> evento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
