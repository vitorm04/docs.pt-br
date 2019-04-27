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
ms.openlocfilehash: ef22114b582ebfc9714dedc0cb6e66594d945ca1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905340"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="3fe2a-102">Método ICeeGen::GetStringSection</span><span class="sxs-lookup"><span data-stu-id="3fe2a-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="3fe2a-103">Obtém uma representação de cadeia de caracteres da seção de código referenciada pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="3fe2a-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="3fe2a-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="3fe2a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe2a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fe2a-105">Syntax</span></span>  
  
```  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fe2a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fe2a-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="3fe2a-107">[no, out] O identificador para a seção de código.</span><span class="sxs-lookup"><span data-stu-id="3fe2a-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fe2a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fe2a-108">Requirements</span></span>  
 <span data-ttu-id="3fe2a-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fe2a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fe2a-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3fe2a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fe2a-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3fe2a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fe2a-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fe2a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe2a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fe2a-113">See also</span></span>

- [<span data-ttu-id="3fe2a-114">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="3fe2a-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
