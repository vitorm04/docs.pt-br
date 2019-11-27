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
ms.openlocfilehash: ff6932b6040a19e0ccda2f8d2140fa131cdd9224
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450070"
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
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [entrada, saída] Um ponteiro para o enumerador. Isso deve ser nulo para a primeira chamada deste método.  
  
 `mb`  
 no Um token MethodDef que limita o escopo da enumeração.  
  
 `rEventProp`  
 fora A matriz usada para armazenar os eventos ou as propriedades.  
  
 `cMax`  
 no O tamanho máximo da matriz de `rEventProp`.  
  
 `pcEventProp`  
 fora O número de eventos ou Propriedades retornados em `rEventProp`.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` retornado com êxito.|  
|`S_FALSE`|Não há eventos ou propriedades para enumerar. Nesse caso, `pcEventProp` é zero.|  
  
## <a name="remarks"></a>Comentários  
 Muitos tipos de Common Language Runtime definem eventos de`Changed` de *Propriedade* e `On`métodos de`Changed` de *Propriedade* relacionados a suas propriedades. Por exemplo, o tipo de <xref:System.Windows.Forms.Control?displayProperty=nameWithType> define uma propriedade <xref:System.Windows.Forms.Control.Font%2A>, um evento <xref:System.Windows.Forms.Control.FontChanged> e um método <xref:System.Windows.Forms.Control.OnFontChanged%2A>. O método do acessador set da propriedade <xref:System.Windows.Forms.Control.Font%2A> chama <xref:System.Windows.Forms.Control.OnFontChanged%2A> método, que, por sua vez, gera o evento <xref:System.Windows.Forms.Control.FontChanged>. Você chamaria `EnumMethodSemantics` usando o MethodDef para <xref:System.Windows.Forms.Control.OnFontChanged%2A> para obter referências à propriedade <xref:System.Windows.Forms.Control.Font%2A> e ao evento <xref:System.Windows.Forms.Control.FontChanged>.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
