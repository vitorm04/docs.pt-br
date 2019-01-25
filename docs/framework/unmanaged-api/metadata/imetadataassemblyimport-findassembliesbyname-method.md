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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 454391eb7a5f1821438837c8fb7e5f8bad6b5723
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651650"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>Método IMetaDataAssemblyImport::FindAssembliesByName
Obtém uma matriz de assemblies com especificado `szAssemblyName` parâmetro, usando as regras padrão empregadas pelo common language runtime (CLR) para resolver referências.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szAppBase`  
 [in] O diretório raiz no qual pesquisar o assembly determinado. Se esse valor é definido como `null`, `FindAssembliesByName` ficará apenas no cache de assembly global para o assembly.  
  
 `szPrivateBin`  
 [in] Uma lista de subdiretórios separados por ponto-e-vírgula (por exemplo, "bin; bin2"), sob o diretório raiz, no qual pesquisar o assembly. Esses diretórios são investigados, além daqueles especificados nas regras de investigação de padrão.  
  
 `szAssemblyName`  
 [in] O nome do assembly para localizar. O formato dessa cadeia de caracteres é definido na página de referência de classe para <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] Uma matriz do tipo [IUnknown](/cpp/atl/iunknown) na qual colocar o `IMetadataAssemblyImport` ponteiros de interface.  
  
 `cMax`  
 [out] O número máximo de ponteiros de interface que pode ser colocado em `ppIUnk`.  
  
 `pcAssemblies`  
 [out] O número de ponteiros de interface retornado. Ou seja, o número de ponteiros de interface realmente colocados nos `ppIUnk`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` retornado com êxito.|  
|`S_FALSE`|Não há nenhum assembly.|  
  
## <a name="remarks"></a>Comentários  
 Recebe um nome de assembly, o `FindAssembliesByName` método encontra o assembly, seguindo as regras padrão para resolver referências de assembly. (Para obter mais informações, consulte [como o tempo de execução Localiza Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permite que o chamador configurar vários aspectos do contexto de resolvedor de assembly, como o caminho de pesquisa de base e privada de aplicativo.  
  
 O `FindAssembliesByName` método requer que o CLR a ser inicializado no processo para invocar a lógica de resolução de assembly. Portanto, você deve chamar [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passando COINITEE_DEFAULT) antes de chamar `FindAssembliesByName`e, em seguida, execute com uma chamada para [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` Retorna um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) ponteiro para o arquivo que contém o manifesto do assembly para o nome do assembly que é passado. Se o nome do assembly determinado não for totalmente especificado (por exemplo, se ele não inclui uma versão), vários assemblies podem ser retornados.  
  
 `FindAssembliesByName` é normalmente usado por um compilador que tenta localizar um assembly referenciado em tempo de compilação.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Como o tempo de execução localiza assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
