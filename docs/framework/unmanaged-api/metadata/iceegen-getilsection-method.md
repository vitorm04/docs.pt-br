---
title: Método ICeeGen::GetIlSection
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bddb782e13b4e7400c7e4a8128dc333efc8141d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746182"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="a3ba9-102">Método ICeeGen::GetIlSection</span><span class="sxs-lookup"><span data-stu-id="a3ba9-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="a3ba9-103">Obtém a seção do código de idioma intermediário base referenciada pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="a3ba9-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="a3ba9-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="a3ba9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ba9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3ba9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3ba9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3ba9-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="a3ba9-107">[in] O identificador para a seção para obter.</span><span class="sxs-lookup"><span data-stu-id="a3ba9-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3ba9-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3ba9-108">Requirements</span></span>  
 <span data-ttu-id="a3ba9-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3ba9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3ba9-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a3ba9-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3ba9-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a3ba9-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a3ba9-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3ba9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ba9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3ba9-113">See also</span></span>

- [<span data-ttu-id="a3ba9-114">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="a3ba9-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
