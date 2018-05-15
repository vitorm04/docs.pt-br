---
title: Método ICeeGen::EmitString
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1dccb2a3a3f3aaf0f209c8f3543056ab81c562dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="3ca08-102">Método ICeeGen::EmitString</span><span class="sxs-lookup"><span data-stu-id="3ca08-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="3ca08-103">Emite a cadeia de caracteres especificada para a base de código.</span><span class="sxs-lookup"><span data-stu-id="3ca08-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="3ca08-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="3ca08-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ca08-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ca08-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ca08-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3ca08-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="3ca08-107">[in] A cadeia de caracteres de emissão.</span><span class="sxs-lookup"><span data-stu-id="3ca08-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="3ca08-108">[out] O endereço virtual relativo da cadeia de caracteres emitido.</span><span class="sxs-lookup"><span data-stu-id="3ca08-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ca08-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ca08-109">Requirements</span></span>  
 <span data-ttu-id="3ca08-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ca08-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ca08-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ca08-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ca08-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3ca08-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ca08-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ca08-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca08-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ca08-114">See Also</span></span>  
 [<span data-ttu-id="3ca08-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="3ca08-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
