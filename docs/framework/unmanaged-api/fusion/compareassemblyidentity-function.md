---
title: "Função CompareAssemblyIdentity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: CompareAssemblyIdentity
helpviewer_keywords: CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 266868a65a0db75b57d46d92a469b4b6ceaa88e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="compareassemblyidentity-function"></a>Função CompareAssemblyIdentity
Compara duas identidades de assembly para determinar se eles são equivalentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwzAssemblyIdentity1`  
 [in] A identidade textual do primeiro conjunto na comparação.  
  
 `fUnified1`  
 [in] Um sinalizador booleano que indica a união de usuário especificado para `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 [in] A identidade textual do segundo assembly na comparação.  
  
 `fUnified2`  
 [in] Um sinalizador booleano que indica a união de usuário especificado para `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 [out] Um sinalizador booliano que indica se os dois assemblies são equivalentes.  
  
 `pResult`  
 [out] Um [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeração que contém informações detalhadas sobre a comparação.  
  
## <a name="return-value"></a>Valor de retorno  
 `pfEquivalent`Retorna um valor booliano que indica se os dois assemblies são equivalentes. `pResult`Retorna um do `AssemblyComparisonResult` valores, para fornecer um motivo mais detalhado para o valor de `pfEquivalent`.  
  
## <a name="remarks"></a>Comentários  
 `CompareAssemblyIdentity`verifica se `pwzAssemblyIdentity1` e `pwzAssemblyIdentity2` são equivalentes. `pfEquivalent`é definido como `true` em uma ou mais das seguintes condições:  
  
-   As identidades de duas assembly são equivalentes. Para assemblies de nomeados forte, equivalência requer o nome do assembly, versão, token de chave pública e a cultura a ser idênticos. Para assemblies nomeados simplesmente, equivalência requer uma correspondência no nome do assembly e cultura.  
  
-   Ambas as identidades de assembly, consulte assemblies que são executados no .NET Framework. Essa condição retornará `true` mesmo se os números de versão do assembly não coincidem.  
  
-   Os dois assemblies não são assemblies gerenciados, mas `fUnified1` ou `fUnified2` foi definido como `true`.  
  
 O `fUnified` sinalizador indica que todos os números de versão até o número de versão do assembly de nome forte são considerados equivalentes para o assembly de nome forte. Por exemplo, se o valor de `pwzAssemblyIndentity1` é "MyAssembly, versão = 3.0.0.0, culture = neutral, publicKeyToken =..." e o valor de `fUnified1` é `true`, isso indica que todas as versões do MyAssembly da versão 0.0.0.0 para 3.0.0.0 devem ser tratados como equivalentes. Nesse caso, se `pwzAssemblyIndentity2` refere-se ao mesmo assembly como `pwzAssemblyIndentity1`, exceto que ele tem um número de versão inferior, `pfEquivalent` é definido como `true`. Se `pwzAssemblyIdentity2` refere-se a um número de versão superior, `pfEquivalent` é definido como `true` somente se o valor de `fUnified2` é `true`.  
  
 O `pResult` parâmetro inclui informações específicas sobre por que os dois assemblies são considerados equivalente ou não equivalente. Para obter mais informações, consulte [enumeração AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [Enumeração AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
