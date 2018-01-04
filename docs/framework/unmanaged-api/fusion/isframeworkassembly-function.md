---
title: "Função IsFrameworkAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IsFrameworkAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IsFrameworkAssembly
helpviewer_keywords: IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa077ce13031772ec2ea20708c1dbd29da02d32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="1ffe9-102">Função IsFrameworkAssembly</span><span class="sxs-lookup"><span data-stu-id="1ffe9-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="1ffe9-103">Obtém um valor que indica se o assembly especificado é gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1ffe9-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ffe9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ffe9-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ffe9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ffe9-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="1ffe9-106">[in] O nome do assembly para verificar.</span><span class="sxs-lookup"><span data-stu-id="1ffe9-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="1ffe9-107">[out] Um valor booliano que indica se o assembly é gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1ffe9-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="1ffe9-108">[in] Uma cadeia de caracteres uncanonicalized que contém a identidade exclusiva do assembly.</span><span class="sxs-lookup"><span data-stu-id="1ffe9-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="1ffe9-109">[in] O tamanho do `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="1ffe9-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ffe9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ffe9-110">Remarks</span></span>  
 <span data-ttu-id="1ffe9-111">O `pwzAssemblyReference` parâmetro é um ponteiro para uma cadeia de caracteres que contém o nome de um assembly.</span><span class="sxs-lookup"><span data-stu-id="1ffe9-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="1ffe9-112">Se esse assembly é parte do .NET Framework, o `pbIsFrameworkAssembly` parâmetro conterá um valor booliano de `true`.</span><span class="sxs-lookup"><span data-stu-id="1ffe9-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="1ffe9-113">Se o assembly nomeado não é parte do .NET Framework, ou se o `pwzAssemblyReference` parâmetro não nomeia um assembly, `pbIsFrameworkAssembly` conterá um valor booliano de `false`.</span><span class="sxs-lookup"><span data-stu-id="1ffe9-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ffe9-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ffe9-114">Requirements</span></span>  
 <span data-ttu-id="1ffe9-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ffe9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffe9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ffe9-116">See Also</span></span>  
 [<span data-ttu-id="1ffe9-117">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="1ffe9-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
