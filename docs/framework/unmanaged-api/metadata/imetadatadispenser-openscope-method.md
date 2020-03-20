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
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175935"
---
# <a name="imetadatadispenseropenscope-method"></a>Método IMetaDataDispenser::OpenScope
Abre um arquivo existente no disco e mapeia seus metadados na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `szScope`  
 [em] O nome do arquivo a ser aberto. O arquivo deve conter metadados de tempo de execução de idioma comum (CLR).  
  
 `dwOpenFlags`  
 [em] Um valor da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) para especificar o modo (ler, gravar e assim por diante) para abertura.  
  
 `riid`  
 [em] O IID da interface de metadados desejada a ser devolvida; o chamador usará a interface para importar (ler) ou emitir metadados (gravar).  
  
 O valor `riid` de deve especificar uma das interfaces "importação" ou "emitir". Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [fora] O ponteiro para a interface retornada.  
  
## <a name="remarks"></a>Comentários  
 A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces de "importação" ou adicionada ao uso de métodos a partir de uma das interfaces "emitidas".  
  
 Se o arquivo de destino não contiver metadados CLR, o `OpenScope` método falhará.  
  
 Na versão .NET Framework 1.0 e versão 1.1, `dwOpenFlags` se um escopo for aberto com set de Read, ele é elegível para compartilhar. Ou seja, se `OpenScope` chamadas subseqüentes para passar em nome de um arquivo que foi aberta anteriormente, o escopo existente é reutilizado e um novo conjunto de estruturas de dados não é criado. No entanto, problemas podem surgir devido a esse compartilhamento.  
  
 Na versão .NET Framework 2.0, `dwOpenFlags` os escopos abertos com set de read não são mais compartilhados. Use o valor de ReadOnly para permitir que o escopo seja compartilhado. Quando um escopo é compartilhado, as consultas que usam interfaces de metadados "ler/gravar" falharão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
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
