---
title: Método ICeeGen::GetString
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: b7b15261d825c1bd5f217c4cecd82ed36a716d0e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008255"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="4afa5-102">Método ICeeGen::GetString</span><span class="sxs-lookup"><span data-stu-id="4afa5-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="4afa5-103">Obtém a cadeia de caracteres armazenada no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="4afa5-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="4afa5-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="4afa5-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4afa5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4afa5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4afa5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4afa5-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="4afa5-107">no O endereço virtual relativo da cadeia de caracteres a ser retornada.</span><span class="sxs-lookup"><span data-stu-id="4afa5-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="4afa5-108">fora A cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="4afa5-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4afa5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4afa5-109">Requirements</span></span>  
 <span data-ttu-id="4afa5-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4afa5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4afa5-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4afa5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4afa5-112">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4afa5-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4afa5-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4afa5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4afa5-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="4afa5-114">See also</span></span>

- [<span data-ttu-id="4afa5-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="4afa5-115">ICeeGen Interface</span></span>](iceegen-interface.md)
