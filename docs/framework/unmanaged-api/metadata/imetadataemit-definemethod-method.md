---
title: Método IMetaDataEmit::DefineMethod
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cdd8f8a1120e3e6e82c87cc02afa5c503493da1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719827"
---
# <a name="imetadataemitdefinemethod-method"></a>Método IMetaDataEmit::DefineMethod
Cria uma definição para um método ou uma função global com a assinatura especificada e retorna um token para essa definição de método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O `mdTypedef` token da classe pai ou a interface pai do método. Definir `td` para `mdTokenNil`, se você estiver definindo uma função global.  
  
 `szName`  
 [in] O nome do membro em Unicode.  
  
 `dwMethodFlags`  
 [in] Um valor igual a [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração que especifica os atributos do método ou função global.  
  
 `pvSigBlob`  
 [in] A assinatura do método. A assinatura é mantida como fornecidos. Se você precisar especificar informações adicionais para quaisquer parâmetros, use o [imetadataemit:: Setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) método.  
  
 `cbSigBlob`  
 [in] A contagem de bytes em `pvSigBlob`.  
  
 `ulCodeRVA`  
 [in] O endereço do código.  
  
 `dwImplFlags`  
 [in] Um valor igual a [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeração que especifica os recursos de implementação do método.  
  
 `pmd`  
 [out] O token de membro.  
  
## <a name="remarks"></a>Comentários  
 A API de metadados garante para persistir os métodos na mesma ordem conforme o chamador emite-los para uma determinada classe delimitadora ou interface, que é especificado no `td` parâmetro.  
  
 Informações adicionais sobre o uso do `DefineMethod` e configurações de parâmetro específica é fornecido abaixo.  
  
## <a name="slots-in-the-v-table"></a>Slots na tabela V  
 O tempo de execução usa as definições de método para configurar os slots de v-table. No caso em que um ou mais slots precisam ser ignorada, como para preservar a paridade com o layout de interface COM um método fictício é definido para ocupar o slot ou slots da tabela v. Defina a `dwMethodFlags` para o `mdRTSpecialName` valor da [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração e especifique o nome como:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 em que *SequenceNumber* é o número de sequência do método e *CountOfSlots* é o número de slots para ignorar a tabela v. Se *CountOfSlots* é omitido, 1 será pressuposto. Esses métodos fictícios não estão acessíveis pelo código gerenciado ou e qualquer tentativa de chamá-los, a partir do código gerenciado ou não gerenciado, gera uma exceção. Sua única finalidade é ocupam espaço na tabela v que o tempo de execução gera para integração COM.  
  
## <a name="duplicate-methods"></a>Métodos duplicados  
 Você não deve definir métodos duplicados. Ou seja, você não deve chamar `DefineMethod` com um conjunto duplicado de valores de `td`, `wzName`, e `pvSig` parâmetros. (Esses três parâmetros juntos definem exclusivamente o método.). No entanto, você pode usar um triplo duplicado desde que, para uma das definições de método, você deve definir a `mdPrivateScope` bit no `dwMethodFlags` parâmetro. (O `mdPrivateScope` bit significa que o compilador não emitirá uma referência a essa definição de método.)  
  
## <a name="method-implementation-information"></a>Informações de implementação de método  
 Informações sobre a implementação do método geralmente não são conhecidas no momento em que o método é declarado. Portanto, não é necessário passar valores de `ulCodeRVA` e `dwImplFlags` parâmetros ao chamar `DefineMethod`. Os valores podem ser fornecidos posteriormente por meio [imetadataemit:: Setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [imetadataemit:: Setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), conforme apropriado.  
  
 Em algumas situações, como invocação de plataforma (PInvoke) ou cenários de interoperabilidade COM, o corpo do método não será fornecido, e `ulCodeRVA` deve ser definido como zero. Nessas situações, o método deve não ser marcado como abstratos, porque o tempo de execução localizará a implementação.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definindo um método para PInvoke  
 Para cada função não gerenciada a ser chamado por meio do PInvoke, você deve definir um método gerenciado que representa a função de destino não gerenciado. Para definir o método gerenciado, use `DefineMethod` com alguns dos parâmetros definidos para determinados valores, dependendo de como o PInvoke é usado:  
  
-   Verdadeiro PInvoke - envolve a invocação de um método externo não gerenciado que reside em uma DLL não gerenciada.  
  
-   PInvoke local - envolve a invocação de um método nativo não gerenciado que está incorporado no módulo gerenciado atual.  
  
 As configurações de parâmetro são fornecidas na tabela a seguir.  
  
|Parâmetro|Valores para verdadeiro PInvoke|Valores de PInvoke local|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Definir `mdStatic`; desmarque `mdSynchronized` e `mdAbstract`.|  
|`pvSigBlob`|Tipos gerenciados do válido common language runtime (CLR) assinatura de um método com parâmetros que são válidos.|Tipos gerenciados de uma assinatura de método do CLR válida com parâmetros que são válidos.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Definir `miCil` e `miManaged`.|Definir `miNative` e `miUnmanaged`.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
