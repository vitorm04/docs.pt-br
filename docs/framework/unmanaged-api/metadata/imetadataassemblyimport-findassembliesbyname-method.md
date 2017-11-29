---
title: "Método IMetaDataAssemblyImport::FindAssembliesByName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindAssembliesByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3b957430e66e4381a9be33ceb687d7aecba53a4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>Método IMetaDataAssemblyImport::FindAssembliesByName
Obtém uma matriz de assemblies com especificado `szAssemblyName` parâmetro, usando as regras padrão usadas pelo common language runtime (CLR) para resolver referências.  
  
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
 [in] O diretório raiz no qual procurar o assembly fornecido. Se esse valor é definido como `null`, `FindAssembliesByName` parecerá apenas no cache de assembly global para o assembly.  
  
 `szPrivateBin`  
 [in] Uma lista de subdiretórios separados por ponto-e-vírgula (por exemplo, "bin; bin2"), no diretório raiz da pesquisa para o assembly. Esses diretórios são investigados além daqueles especificados no padrão de regras de investigação.  
  
 `szAssemblyName`  
 [in] O nome do assembly para localizar. O formato dessa cadeia de caracteres é definido na página de referência de classe para <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] Uma matriz do tipo <<!--zzxref:IUnknown --> `IUnknown`> na qual colocar o `IMetadataAssemblyImport` ponteiros de interface.  
  
 `cMax`  
 [out] O número máximo de ponteiros de interface que pode ser colocado em `ppIUnk`.  
  
 `pcAssemblies`  
 [out] O número de ponteiros de interface é retornado. Ou seja, o número de ponteiros de interface, na verdade, colocados em `ppIUnk`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`retornou com êxito.|  
|`S_FALSE`|Não há nenhum assembly.|  
  
## <a name="remarks"></a>Comentários  
 Recebe um nome de assembly, o `FindAssembliesByName` método encontra o assembly, seguindo as regras padrão para resolver referências de assembly. (Para obter mais informações, consulte [como o tempo de execução Localiza Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permite que o chamador configurar vários aspectos do contexto de resolvedor de assembly, como caminho de pesquisa de base e privados do aplicativo.  
  
 O `FindAssembliesByName` método requer que o CLR a ser inicializado no processo para invocar a lógica de resolução de assembly. Portanto, você deve chamar [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passando COINITEE_DEFAULT) antes de chamar `FindAssembliesByName`e, em seguida, execute com uma chamada para [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`Retorna um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) ponteiro para o arquivo que contém o manifesto do assembly para o nome do assembly que é transmitido. Se o nome do assembly fornecido não é totalmente especificado (por exemplo, se ele não inclui uma versão), vários assemblies podem ser retornados.  
  
 `FindAssembliesByName`é normalmente usado por um compilador que tenta localizar um assembly referenciado em tempo de compilação.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Como o tempo de execução localiza assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
