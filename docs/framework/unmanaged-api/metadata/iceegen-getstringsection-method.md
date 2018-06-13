---
title: Método ICeeGen::GetStringSection
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a8617c9e818ec514c912a85373c916559d89df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443031"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="0a65b-102">Método ICeeGen::GetStringSection</span><span class="sxs-lookup"><span data-stu-id="0a65b-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="0a65b-103">Obtém uma representação de cadeia de caracteres da seção de código referenciada pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="0a65b-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="0a65b-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="0a65b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a65b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a65b-105">Syntax</span></span>  
  
```  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a65b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0a65b-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="0a65b-107">[out no] O identificador para a seção de código.</span><span class="sxs-lookup"><span data-stu-id="0a65b-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a65b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a65b-108">Requirements</span></span>  
 <span data-ttu-id="0a65b-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a65b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a65b-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0a65b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a65b-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0a65b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0a65b-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a65b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a65b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a65b-113">See Also</span></span>  
 [<span data-ttu-id="0a65b-114">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="0a65b-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
