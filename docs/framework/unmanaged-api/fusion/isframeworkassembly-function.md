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
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796324"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="4b31e-102">Função IsFrameworkAssembly</span><span class="sxs-lookup"><span data-stu-id="4b31e-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="4b31e-103">Obtém um valor que indica se o assembly especificado é gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4b31e-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b31e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b31e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b31e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b31e-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="4b31e-106">no O nome do assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="4b31e-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="4b31e-107">fora Um valor booliano que indica se o assembly é gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4b31e-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="4b31e-108">no Uma cadeia de caracteres não canônica que contém a identidade exclusiva do assembly.</span><span class="sxs-lookup"><span data-stu-id="4b31e-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="4b31e-109">[in] O tamanho do `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="4b31e-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b31e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b31e-110">Remarks</span></span>  
 <span data-ttu-id="4b31e-111">O `pwzAssemblyReference` parâmetro é um ponteiro para uma cadeia de caracteres que contém o nome de um assembly.</span><span class="sxs-lookup"><span data-stu-id="4b31e-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="4b31e-112">Se esse assembly fizer parte do .NET Framework, o `pbIsFrameworkAssembly` parâmetro conterá um valor booliano de. `true`</span><span class="sxs-lookup"><span data-stu-id="4b31e-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="4b31e-113">Se o assembly nomeado não fizer parte do .NET Framework, ou se o `pwzAssemblyReference` parâmetro não nomear um assembly, `pbIsFrameworkAssembly` conterá um valor booliano de `false`.</span><span class="sxs-lookup"><span data-stu-id="4b31e-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b31e-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b31e-114">Requirements</span></span>  
 <span data-ttu-id="4b31e-115">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b31e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b31e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b31e-116">See also</span></span>

- [<span data-ttu-id="4b31e-117">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="4b31e-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
