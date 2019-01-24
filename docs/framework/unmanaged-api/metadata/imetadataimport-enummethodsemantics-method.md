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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3c20e2787eb8071b10e06b980572c347959fe3c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619442"
---
# <a name="imetadataimportenummethodsemantics-method"></a>Método IMetaDataImport::EnumMethodSemantics
Enumera as propriedades e os eventos de alteração de propriedade à qual o método especificado está relacionado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [no, out] Um ponteiro para o enumerador. Isso deve ser NULL para a primeira chamada desse método.  
  
 `mb`  
 [in] Um token de MethodDef que limita o escopo da enumeração.  
  
 `rEventProp`  
 [out] A matriz usada para armazenar os eventos ou propriedades.  
  
 `cMax`  
 [in] O tamanho máximo da `rEventProp` matriz.  
  
 `pcEventProp`  
 [out] O número de eventos ou propriedades retornadas no `rEventProp`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` retornado com êxito.|  
|`S_FALSE`|Não há eventos ou propriedades para enumerar. Nesse caso, `pcEventProp` é zero.|  
  
## <a name="remarks"></a>Comentários  
 Definem muitos tipos common language runtime *propriedade* `Changed` eventos e `On` *propriedade* `Changed` métodos relacionados às suas propriedades. Por exemplo, o <xref:System.Windows.Forms.Control?displayProperty=nameWithType> tipo define uma <xref:System.Windows.Forms.Control.Font%2A> propriedade, um <xref:System.Windows.Forms.Control.FontChanged> eventos e um <xref:System.Windows.Forms.Control.OnFontChanged%2A> método. O método de acessador set do <xref:System.Windows.Forms.Control.Font%2A> chamadas de propriedade <xref:System.Windows.Forms.Control.OnFontChanged%2A> método, que por sua vez dispara o <xref:System.Windows.Forms.Control.FontChanged> eventos. Você chamaria `EnumMethodSemantics` usando o MethodDef para <xref:System.Windows.Forms.Control.OnFontChanged%2A> para obter referências para o <xref:System.Windows.Forms.Control.Font%2A> propriedade e o <xref:System.Windows.Forms.Control.FontChanged> eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
