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
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177673"
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
  
## <a name="parameters"></a>parâmetros  
 `td`  
 [em] O `mdTypedef` token da classe pai ou interface pai do método. Definir `td` `mdTokenNil`para , se você estiver definindo uma função global.  
  
 `szName`  
 [em] O nome do membro no Unicode.  
  
 `dwMethodFlags`  
 [em] Um valor da enumeração [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) que especifica os atributos do método ou da função global.  
  
 `pvSigBlob`  
 [em] A assinatura do método. A assinatura é persistida conforme fornecido. Se você precisar especificar informações adicionais para quaisquer parâmetros, use o método [IMetaDataEmit::SetParamProps.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)  
  
 `cbSigBlob`  
 [em] A contagem de `pvSigBlob`bytes em .  
  
 `ulCodeRVA`  
 [em] O endereço do código.  
  
 `dwImplFlags`  
 [em] Um valor da enumeração [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) que especifica os recursos de implementação do método.  
  
 `pmd`  
 [fora] O símbolo do membro.  
  
## <a name="remarks"></a>Comentários  
 A API de metadados garante a persistência de métodos na mesma ordem que o chamador emite-os para uma determinada classe ou interface de fechamento, que é especificada no `td` parâmetro.  
  
 Informações adicionais sobre `DefineMethod` o uso e configurações de parâmetros específicos são dadas abaixo.  
  
## <a name="slots-in-the-v-table"></a>Ranhuras na tabela V  
 O tempo de execução usa definições de método para configurar slots de tabela v. No caso de um ou mais slots precisarem ser pulados, como preservar a paridade com um layout de interface COM, um método manequim é definido para assumir o slot ou slots na tabela v; defina `dwMethodFlags` o `mdRTSpecialName` valor da enumeração [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) e especifique o nome como:  
  
 _VtblGap\<*seqüêncianúmero*>\<\_*de números de númerosdeslots*>
  
 onde *SequenceNumber* é o número de seqüência do método e *CountOfSlots* é o número de slots a serem pulados na tabela v. Se *CountOfSlots* for omitido, 1 é assumido. Esses métodos falsos não podem ser chamados de código gerenciado ou não e qualquer tentativa de chamá-los, de código gerenciado ou não gerenciado, gera uma exceção. Seu único propósito é retomar espaço na tabela v que o tempo de execução gera para a integração COM.  
  
## <a name="duplicate-methods"></a>Métodos duplicados  
 Você não deve definir métodos duplicados. Ou seja, você `DefineMethod` não deve ligar com `td`um `wzName`conjunto `pvSig` duplicado de valores nos parâmetros e parâmetros. (Esses três parâmetros juntos definem exclusivamente o método.). No entanto, você pode usar uma duplicata tripla desde `mdPrivateScope` que, `dwMethodFlags` para uma das definições do método, você defina a broca no parâmetro. (O `mdPrivateScope` bit significa que o compilador não emite uma referência a essa definição de método.)  
  
## <a name="method-implementation-information"></a>Informações de implementação do método  
 Muitas vezes não são conhecidas informações sobre a implementação do método no momento em que o método é declarado. Portanto, você não precisa passar valores `dwImplFlags` nos `DefineMethod`parâmetros e parâmetros ao `ulCodeRVA` ligar . Os valores podem ser fornecidos posteriormente através do [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), conforme apropriado.  
  
 Em algumas situações, como a invocação da plataforma (PInvoke) ou cenários `ulCodeRVA` de interop COM, o corpo do método não será fornecido e deve ser definido como zero. Nessas situações, o método não deve ser marcado como abstrato, pois o tempo de execução localizará a implementação.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definindo um método para PInvoke  
 Para cada função não gerenciada a ser chamada através do PInvoke, você deve definir um método gerenciado que represente a função não gerenciada de destino. Para definir o método `DefineMethod` gerenciado, use com alguns dos parâmetros definidos para determinados valores, dependendo da forma como o PInvoke é usado:  
  
- True PInvoke - envolve a invocação de um método externo não gerenciado que reside em um DLL não gerenciado.  
  
- PInvoke local - envolve a invocação de um método nativo não gerenciado que está incorporado no módulo gerenciado atual.  
  
 As configurações dos parâmetros são fornecidas na tabela a seguir.  
  
|Parâmetro|Valores para pinvoke verdadeiro|Valores para PInvoke local|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Conjunto `mdStatic`; claro `mdSynchronized` `mdAbstract`e .|  
|`pvSigBlob`|Uma assinatura de método de tempo de execução de idioma comum válido (CLR) com parâmetros que são tipos gerenciados válidos.|Uma assinatura de método CLR válida com parâmetros que são tipos gerenciados válidos.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Definir `miCil` e `miManaged`.|Definir `miNative` e `miUnmanaged`.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
