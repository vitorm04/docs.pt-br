---
title: "Método IMetaDataEmit::DefineMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fa136f5e6669e58ef709db5b53f538804cfcac2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemethod-method"></a>Método IMetaDataEmit::DefineMethod
Cria uma definição para um método ou função global com a assinatura especificada e retorna um token para que a definição de método.  
  
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
 [in] O `mdTypedef` token da classe pai ou interface pai do método. Definir `td` para `mdTokenNil`, se você estiver definindo uma função global.  
  
 `szName`  
 [in] O nome de membro em Unicode.  
  
 `dwMethodFlags`  
 [in] Um valor de [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração que especifica os atributos de método ou função global.  
  
 `pvSigBlob`  
 [in] A assinatura do método. A assinatura é mantida conforme fornecido. Se você precisar especificar informações adicionais para qualquer parâmetro, use o [Setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) método.  
  
 `cbSigBlob`  
 [in] A contagem de bytes em `pvSigBlob`.  
  
 `ulCodeRVA`  
 [in] O endereço do código.  
  
 `dwImplFlags`  
 [in] Um valor de [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeração que especifica os recursos de implementação do método.  
  
 `pmd`  
 [out] O token de membro.  
  
## <a name="remarks"></a>Comentários  
 Os metadados de API garante persistem métodos na mesma ordem em que o chamador emite-los para uma determinada classe de delimitador ou a interface, que é especificada no `td` parâmetro.  
  
 Informações adicionais sobre o uso do `DefineMethod` e configurações de parâmetro específico são indicados abaixo.  
  
## <a name="slots-in-the-v-table"></a>Slots da tabela V  
 O tempo de execução usa definições de método para configurar os slots da tabela v. No caso onde um ou mais slots precisam ser ignorada, como para preservar a paridade com o layout de interface COM um método fictício é definido para o slot ou slots da tabela v. definir o `dwMethodFlags` para o `mdRTSpecialName` valor o [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração e especifique o nome como:  
  
 VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>  
  
 onde *SequenceNumber* é o número de sequência do método e *CountOfSlots* é o número de slots para ignorar na tabela v. Se *CountOfSlots* for omitido, 1 é assumido. Esses métodos fictícios não pode ser chamados de código gerenciado ou e qualquer tentativa de chamá-los, o código gerenciado ou, gera uma exceção. Seu único propósito é ocupam espaço no v-table gerados para integração COM o tempo de execução.  
  
## <a name="duplicate-methods"></a>Métodos duplicados  
 Você não deve definir métodos duplicados. Ou seja, você não deve chamar `DefineMethod` com um conjunto duplicado dos valores a `td`, `wzName`, e `pvSig` parâmetros. (Esses três parâmetros juntos definem exclusivamente o método.). No entanto, você pode usar um triplo duplicado desde que, para uma das definições de método, você deve definir o `mdPrivateScope` bit no `dwMethodFlags` parâmetro. (O `mdPrivateScope` bit significa que o compilador não emitirá uma referência a essa definição de método.)  
  
## <a name="method-implementation-information"></a>Informações de implementação de método  
 Informações sobre a implementação do método geralmente não são conhecidas no momento em que o método for declarado. Portanto, você não precisa passar valores de `ulCodeRVA` e `dwImplFlags` parâmetros ao chamar `DefineMethod`. Os valores podem ser fornecidos posteriormente por [: Setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [: Setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), conforme apropriado.  
  
 Em algumas situações, como a invocação de plataforma (PInvoke) ou cenários de interoperabilidade COM, o corpo do método não será fornecido, e `ulCodeRVA` deve ser definido como zero. Nessas situações, o método deve não marcado como abstract, porque o tempo de execução localizará a implementação.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definindo um método de PInvoke  
 Para cada função não gerenciada a ser chamado por meio de PInvoke, você deve definir um método gerenciado que representa a função não gerenciada de destino. Para definir o método gerenciado, use `DefineMethod` com alguns dos parâmetros definidos para determinados valores, dependendo do modo no qual PInvoke é usada:  
  
-   Verdadeiro PInvoke - envolve a invocação de um método externo não gerenciado que reside em uma DLL não gerenciada.  
  
-   PInvoke local - envolve a invocação de um método nativo não gerenciado que é inserido no módulo gerenciado atual.  
  
 As configurações de parâmetro são fornecidas na tabela a seguir.  
  
|Parâmetro|Valores de PInvoke true|Valores de PInvoke local|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Definir `mdStatic`; limpar `mdSynchronized` e `mdAbstract`.|  
|`pvSigBlob`|Tipos gerenciados do válido common language runtime (CLR) assinatura de um método com parâmetros que são válidos.|Tipos gerenciados de uma assinatura de método CLR válida com parâmetros que são válidos.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Definir `miCil` e `miManaged`.|Definir `miNative` e `miUnmanaged`.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
