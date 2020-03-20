---
title: Método IMetaDataInfo::GetFileMapping
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175259"
---
# <a name="imetadatainfogetfilemapping-method"></a>Método IMetaDataInfo::GetFileMapping
Obtém a região de memória do arquivo mapeado e o tipo de mapeamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `ppvData`  
 [fora] Um ponteiro para o início do arquivo mapeado.  
  
 `pcbData`  
 [fora] O tamanho da região mapeada. Se `pdwMappingType` `fmFlat`for, este é o tamanho do arquivo.  
  
 `pdwMappingType`  
 [fora] Um valor [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) que indica o tipo de mapeamento. A implementação atual do tempo de execução `fmFlat`do idioma comum (CLR) sempre retorna . Outros valores são reservados para uso futuro. No entanto, você deve sempre verificar o valor retornado, pois outros valores podem ser habilitados em versões futuras ou versões de serviço.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|Todas as saídas estão preenchidas.|  
|`E_INVALIDARG`|NULL foi passado como um valor de argumento.|  
|`COR_E_NOTSUPPORTED`|A implementação do CLR não pode fornecer informações sobre a região da memória. Isso pode ocorrer pelos seguintes motivos:<br /><br /> - O escopo dos metadados foi aberto com a `ofWrite` bandeira. `ofCopyMemory`<br />- O escopo dos metadados foi aberto sem a `ofReadOnly` bandeira.<br />- O método [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) foi usado para abrir apenas a parte de metadados do arquivo.<br />- O arquivo não é um arquivo executável portátil (PE). **Nota:**  Essas condições dependem da implementação da CLR, e provavelmente serão enfraquecidas em versões futuras da CLR.|  
  
## <a name="remarks"></a>Comentários  
 A memória `ppvData` que aponta é válida apenas enquanto o escopo de metadados subjacente estiver aberto.  
  
 Para que este método funcione, ao mapear os metadados de um arquivo on-disk na memória, chamando o `ofReadOnly` método [IMetaDataDispenser::OpenScope,](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) você deve especificar o sinalizador e não deve especificar o `ofWrite` ou `ofCopyMemory` sinalizador.  
  
 A escolha do tipo de mapeamento de arquivos para cada escopo é específica para uma determinada implementação da CLR. Não pode ser definido pelo usuário. A implementação atual da `fmFlat` CLR sempre `pdwMappingType`retorna, mas isso pode mudar em versões futuras da CLR ou em futuros lançamentos de serviço de uma determinada versão. Você deve sempre verificar o `pdwMappingType`valor devolvido, pois diferentes tipos terão layouts e deslocamentos diferentes.  
  
 Não é suportado o passe NULA para qualquer um dos três parâmetros. O método `E_INVALIDARG`retorna e nenhuma das saídas está preenchida. Ignorar o tipo de mapeamento ou o tamanho da região pode resultar em término anormal do programa.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataInfo](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [Enumeração CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
