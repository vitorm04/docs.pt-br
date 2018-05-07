---
title: Função IsFrameworkAssembly
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3fd130759ab11b54b597d5c099c33dab93070ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isframeworkassembly-function"></a>Função IsFrameworkAssembly
Obtém um valor que indica se o assembly especificado é gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwzAssemblyReference`  
 [in] O nome do assembly para verificar.  
  
 `pbIsFrameworkAssembly`  
 [out] Um valor booliano que indica se o assembly é gerenciado.  
  
 `pwzFrameworkAssemblyIdentity`  
 [in] Uma cadeia de caracteres uncanonicalized que contém a identidade exclusiva do assembly.  
  
 `pccSize`  
 [in] O tamanho do `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Comentários  
 O `pwzAssemblyReference` parâmetro é um ponteiro para uma cadeia de caracteres que contém o nome de um assembly.  
  
 Se esse assembly é parte do .NET Framework, o `pbIsFrameworkAssembly` parâmetro conterá um valor booliano de `true`.  
  
 Se o assembly nomeado não é parte do .NET Framework, ou se o `pwzAssemblyReference` parâmetro não nomeia um assembly, `pbIsFrameworkAssembly` conterá um valor booliano de `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
## <a name="see-also"></a>Consulte também  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
