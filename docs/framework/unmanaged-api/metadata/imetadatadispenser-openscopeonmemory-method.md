---
title: Método IMetaDataDispenser::OpenScopeOnMemory
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 492c37540ad68b5b134520218eedc59013c68519
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175922"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>Método IMetaDataDispenser::OpenScopeOnMemory
Abre uma área de memória que contém metadados existentes. Ou seja, este método abre uma área especificada de memória na qual os dados existentes são tratados como metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pData`  
 [em] Um ponteiro que especifica o endereço inicial da área de memória.  
  
 `cbData`  
 [em] O tamanho da área de memória, em bytes.  
  
 `dwOpenFlags`  
 [em] Um valor da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) para especificar o modo (ler, gravar e assim por diante) para abertura.  
  
 `riid`  
 [em] O IID da interface de metadados desejada a ser devolvida; o chamador usará a interface para importar (ler) ou emitir metadados (gravar).  
  
 O valor `riid` de deve especificar uma das interfaces "importação" ou "emitir". Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [fora] O ponteiro para a interface retornada.  
  
## <a name="remarks"></a>Comentários  
 A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces de "importação" ou adicionada ao uso de métodos a partir de uma das interfaces "emitidas".  
  
 O `OpenScopeOnMemory` método é semelhante ao [método IMetaDataDispenser::OpenScope,](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) exceto que os metadados de interesse já existem na memória, em vez de em um arquivo em disco.  
  
 Se a área de destino da memória não contiver metadados `OpenScopeOnMemory` de tempo de execução de linguagem comum (CLR), o método falhará.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
