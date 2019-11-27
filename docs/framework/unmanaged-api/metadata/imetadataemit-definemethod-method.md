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
ms.openlocfilehash: c46b075341742aac605537a08b762b3cf47ef35b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431809"
---
# <a name="imetadataemitdefinemethod-method"></a>Método IMetaDataEmit::DefineMethod
Cria uma definição para um método ou função global com a assinatura especificada e retorna um token para essa definição de método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 no O token `mdTypedef` da classe pai ou da interface pai do método. Defina `td` como `mdTokenNil`, se você estiver definindo uma função global.  
  
 `szName`  
 no O nome do membro em Unicode.  
  
 `dwMethodFlags`  
 no Um valor da enumeração [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) que especifica os atributos do método ou da função global.  
  
 `pvSigBlob`  
 no A assinatura do método. A assinatura é persistida conforme fornecido. Se você precisar especificar informações adicionais para quaisquer parâmetros, use o método [IMetaDataEmit:: SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) .  
  
 `cbSigBlob`  
 no A contagem de bytes em `pvSigBlob`.  
  
 `ulCodeRVA`  
 no O endereço do código.  
  
 `dwImplFlags`  
 no Um valor da enumeração [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) que especifica os recursos de implementação do método.  
  
 `pmd`  
 fora O token do membro.  
  
## <a name="remarks"></a>Comentários  
 A API de metadados garante que os métodos persistam na mesma ordem em que o chamador os emite para uma determinada classe ou interface de delimitação, que é especificada no parâmetro `td`.  
  
 Informações adicionais sobre o uso de `DefineMethod` e configurações de parâmetros específicas são fornecidas abaixo.  
  
## <a name="slots-in-the-v-table"></a>Slots na tabela V  
 O tempo de execução usa definições de método para configurar slots de tabela v. No caso em que um ou mais slots precisam ser ignorados, como para preservar a paridade com um layout de interface COM, um método fictício é definido para ocupar o slot ou os slots na tabela v; Defina o `dwMethodFlags` para o valor de `mdRTSpecialName` da enumeração [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) e especifique o nome como:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 em que *SequenceNumber* é o número de sequência do método e *CountOfSlots* é o número de Slots a serem ignorados na tabela v. Se *CountOfSlots* for omitido, 1 será assumido. Esses métodos fictícios não podem ser chamados de código gerenciado ou não gerenciado e qualquer tentativa de chamá-los, a partir de código gerenciado ou não gerenciado, gera uma exceção. Sua única finalidade é ocupar espaço na tabela v que o tempo de execução gera para a integração COM.  
  
## <a name="duplicate-methods"></a>Métodos duplicados  
 Você não deve definir métodos duplicados. Ou seja, você não deve chamar `DefineMethod` com um conjunto duplicado de valores nos parâmetros `td`, `wzName`e `pvSig`. (Esses três parâmetros definem exclusivamente o método.). No entanto, você pode usar um triplo de duplicatas fornecido que, para uma das definições de método, você define o `mdPrivateScope` bit no parâmetro `dwMethodFlags`. (O bit de `mdPrivateScope` significa que o compilador não emitirá uma referência para essa definição de método.)  
  
## <a name="method-implementation-information"></a>Informações de implementação do método  
 As informações sobre a implementação do método geralmente não são conhecidas no momento em que o método é declarado. Portanto, você não precisa passar valores nos parâmetros `ulCodeRVA` e `dwImplFlags` ao chamar `DefineMethod`. Os valores podem ser fornecidos posteriormente por meio de [IMetaDataEmit:: SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit:: SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), conforme apropriado.  
  
 Em algumas situações, como a invocação de plataforma (PInvoke) ou cenários de interoperabilidade COM, o corpo do método não será fornecido e `ulCodeRVA` deverá ser definido como zero. Nessas situações, o método não deve ser marcado como abstrato, pois o tempo de execução localizará a implementação.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definindo um método para PInvoke  
 Para cada função não gerenciada a ser chamada por meio de PInvoke, você deve definir um método gerenciado que representa a função de destino não gerenciada. Para definir o método gerenciado, use `DefineMethod` com alguns dos parâmetros definidos para determinados valores, dependendo da maneira como o PInvoke é usado:  
  
- Verdadeiro PInvoke – envolve a invocação de um método externo não gerenciado que reside em uma DLL não gerenciada.  
  
- PInvoke local – envolve a invocação de um método nativo não gerenciado que é inserido no módulo gerenciado atual.  
  
 As configurações de parâmetro são fornecidas na tabela a seguir.  
  
|Parâmetro|Valores para verdadeiro PInvoke|Valores para o PInvoke local|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Definir `mdStatic`; Desmarque `mdSynchronized` e `mdAbstract`.|  
|`pvSigBlob`|Uma assinatura de método de Common Language Runtime (CLR) válida com parâmetros que são tipos gerenciados válidos.|Uma assinatura de método CLR válida com parâmetros que são tipos gerenciados válidos.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Defina `miCil` e `miManaged`.|Defina `miNative` e `miUnmanaged`.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
