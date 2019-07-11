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
ms.openlocfilehash: 989d046bba1ba3170649e9d908a850bd1177fdd2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773835"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="a880f-102">Função IsFrameworkAssembly</span><span class="sxs-lookup"><span data-stu-id="a880f-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="a880f-103">Obtém um valor que indica se o assembly especificado é gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a880f-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a880f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a880f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a880f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a880f-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="a880f-106">[in] O nome do assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="a880f-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="a880f-107">[out] Um valor booliano que indica se o assembly é gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a880f-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="a880f-108">[in] Uma cadeia de caracteres uncanonicalized que contém a identidade exclusiva do assembly.</span><span class="sxs-lookup"><span data-stu-id="a880f-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="a880f-109">[in] O tamanho do `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a880f-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a880f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a880f-110">Remarks</span></span>  
 <span data-ttu-id="a880f-111">O `pwzAssemblyReference` parâmetro é um ponteiro para uma cadeia de caracteres que contém o nome de um assembly.</span><span class="sxs-lookup"><span data-stu-id="a880f-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="a880f-112">Se esse assembly fizer parte do .NET Framework, o `pbIsFrameworkAssembly` parâmetro conterá um valor booliano de `true`.</span><span class="sxs-lookup"><span data-stu-id="a880f-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="a880f-113">Se o assembly nomeado não é parte do .NET Framework, ou se o `pwzAssemblyReference` parâmetro não nomeia um assembly `pbIsFrameworkAssembly` conterá um valor booliano de `false`.</span><span class="sxs-lookup"><span data-stu-id="a880f-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a880f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a880f-114">Requirements</span></span>  
 <span data-ttu-id="a880f-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a880f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a880f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a880f-116">See also</span></span>

- [<span data-ttu-id="a880f-117">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="a880f-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
