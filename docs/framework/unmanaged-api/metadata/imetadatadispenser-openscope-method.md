---
title: Método IMetaDataDispenser::OpenScope
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5ce1af82631531f8f7105fbf92ba78db3cca437b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442322"
---
# <a name="imetadatadispenseropenscope-method"></a>Método IMetaDataDispenser::OpenScope
Abre um arquivo existente em disco e mapeia seus metadados na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szScope`  
 no O nome do arquivo a ser aberto. O arquivo deve conter metadados de Common Language Runtime (CLR).  
  
 `dwOpenFlags`  
 no Um valor da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) para especificar o modo (leitura, gravação e assim por diante) para abertura.  
  
 `riid`  
 no A IID da interface de metadados desejada a ser retornada; o chamador usará a interface para importar (ler) ou emitir (gravar) metadados.  
  
 O valor de `riid` deve especificar uma das interfaces "Import" ou "Emit". Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.  
  
 `ppIUnk`  
 fora O ponteiro para a interface retornada.  
  
## <a name="remarks"></a>Comentários  
 A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces "Import" ou adicionadas ao uso de métodos de uma das interfaces "Emit".  
  
 Se o arquivo de destino não contiver metadados CLR, o método `OpenScope` falhará.  
  
 No .NET Framework versão 1,0 e 1,1, se um escopo for aberto com `dwOpenFlags` definido como ofRead, ele será elegível para compartilhamento. Ou seja, se as chamadas subsequentes para `OpenScope` passarem o nome de um arquivo que foi aberto anteriormente, o escopo existente será reutilizado e um novo conjunto de estruturas de dados não será criado. No entanto, podem surgir problemas devido a esse compartilhamento.  
  
 No .NET Framework versão 2,0, os escopos abertos com `dwOpenFlags` definidos como ofRead não são mais compartilhados. Use o valor ofReadOnly para permitir que o escopo seja compartilhado. Quando um escopo é compartilhado, as consultas que usam interfaces de metadados de "leitura/gravação" falharão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
