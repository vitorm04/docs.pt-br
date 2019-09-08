---
title: Função CompareAssemblyIdentity
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b52d3af38bd09ce5864c25d27e148dbd7f4639b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795450"
---
# <a name="compareassemblyidentity-function"></a>Função CompareAssemblyIdentity
Compara duas identidades de assembly para determinar se elas são equivalentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pwzAssemblyIdentity1`  
 no A identidade textual do primeiro assembly na comparação.  
  
 `fUnified1`  
 no Um sinalizador booliano que indica a unificação especificada `pwzAssemblyIdentity1`pelo usuário para.  
  
 `pwzAssemblyIdentity2`  
 no A identidade textual do segundo assembly na comparação.  
  
 `fUnified2`  
 no Um sinalizador booliano que indica a unificação especificada `pwzAssemblyIdentity2`pelo usuário para.  
  
 `pfEquivalent`  
 fora Um sinalizador booliano que indica se os dois assemblies são equivalentes.  
  
 `pResult`  
 fora Uma enumeração [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) que contém informações detalhadas sobre a comparação.  
  
## <a name="return-value"></a>Valor de retorno  
 `pfEquivalent`Retorna um valor booliano que indica se os dois assemblies são equivalentes. `pResult`Retorna um dos `AssemblyComparisonResult` valores para fornecer um motivo mais detalhado para o valor de `pfEquivalent`.  
  
## <a name="remarks"></a>Comentários  
 `CompareAssemblyIdentity`verifica se `pwzAssemblyIdentity1` e `pwzAssemblyIdentity2` são equivalentes. `pfEquivalent`é definido como `true` sob uma ou mais das seguintes condições:  
  
- As duas identidades de assembly são equivalentes. Para assemblies com nome forte, a equivalência exige que o nome do assembly, a versão, o token de chave pública e a cultura sejam idênticos. Para apenas assemblies nomeados, a equivalência requer uma correspondência no nome do assembly e na cultura.  
  
- Ambas as identidades do assembly se referem a assemblies que são executados no .NET Framework. Essa condição retorna `true` mesmo que os números de versão do assembly não coincidam.  
  
- Os dois assemblies não são assemblies gerenciados, `fUnified1` mas `fUnified2` ou foram definidos `true`como.  
  
 O `fUnified` sinalizador indica que todos os números de versão até o número de versão do assembly com nome forte são considerados equivalentes ao assembly com nome forte. Por exemplo, se o valor de `pwzAssemblyIndentity1` for "MyAssembly, Version = 3.0.0.0, Culture = neutral, PublicKeyToken =...." e o valor de `fUnified1` for `true`, isso indica que todas as versões de MyAssembly da versão 0.0.0.0 para 3.0.0.0 devem ser Tratado como equivalente. `pwzAssemblyIndentity2` Nesse caso, se se referir ao mesmo assembly como `pwzAssemblyIndentity1`, exceto que ele tem um número de versão inferior, `pfEquivalent` será definido como `true`. Se `pwzAssemblyIdentity2` se referir a um número de `pfEquivalent` versão superior, `true` será definido como somente se `fUnified2` o `true`valor de for.  
  
 O `pResult` parâmetro inclui informações específicas sobre por que os dois assemblies são considerados equivalentes ou não equivalentes. Para obter mais informações, consulte [Enumeração AssemblyComparisonResult](assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Biblioteca** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções estáticas globais de fusão](fusion-global-static-functions.md)
- [Enumeração AssemblyComparisonResult](assemblycomparisonresult-enumeration.md)
