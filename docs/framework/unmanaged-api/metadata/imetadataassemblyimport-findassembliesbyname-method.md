---
title: Método IMetaDataAssemblyImport::FindAssembliesByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177797"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>Método IMetaDataAssemblyImport::FindAssembliesByName
Obtém uma matriz de conjuntos com o parâmetro especificado, `szAssemblyName` usando as regras padrão empregadas pelo tempo de execução da linguagem comum (CLR) para resolver referências.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `szAppBase`  
 [em] O diretório raiz em que procurar a assembléia dada. Se este valor `null`for `FindAssembliesByName` definido como , será olhar apenas no cache de montagem global para a montagem.  
  
 `szPrivateBin`  
 [em] Uma lista de subdiretórios delimitados por ponto e vírgula (por exemplo, bin;bin2), o diretório raiz, no qual procurar a montagem. Esses diretórios são sondados além daqueles especificados nas regras de sondagem padrão.  
  
 `szAssemblyName`  
 [em] O nome da assembléia para encontrar. O formato desta seqüência é definido <xref:System.Reflection.AssemblyName>na página de referência da classe para .  
  
 `ppIUnk`  
 [em] Uma matriz do tipo [IUnknown](/cpp/atl/iunknown) `IMetadataAssemblyImport` para colocar os ponteiros de interface.  
  
 `cMax`  
 [fora] O número máximo de ponteiros de `ppIUnk`interface que podem ser colocados em .  
  
 `pcAssemblies`  
 [fora] O número de ponteiros de interface retornou. Ou seja, o número de ponteiros de interface realmente colocados em `ppIUnk`.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`retornou com sucesso.|  
|`S_FALSE`|Não há assembléias.|  
  
## <a name="remarks"></a>Comentários  
 Dado um nome `FindAssembliesByName` de montagem, o método encontra a montagem seguindo as regras padrão para resolver referências de montagem. (Para obter mais informações, [consulte Como o Runtime localiza conjuntos](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permite que o chamador configure vários aspectos do contexto de resolução de montagem, como base de aplicativo e caminho de pesquisa privado.  
  
 O `FindAssembliesByName` método exige que a CLR seja inicializada no processo, a fim de invocar a lógica de resolução da montagem. Portanto, você deve ligar para [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) `FindAssembliesByName`(passando COINITEE_DEFAULT) antes de ligar e, em seguida, seguir com uma chamada para [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`retorna um ponteiro [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) para o arquivo que contém o manifesto de montagem para o nome de montagem que é passado. Se o nome de montagem dado não for totalmente especificado (por exemplo, se ele não incluir uma versão), vários conjuntos poderão ser retornados.  
  
 `FindAssembliesByName`é comumente usado por um compilador que tenta encontrar um conjunto referenciado no momento da compilação.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Como o runtime localiza assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
