---
title: Função GetRealProcAddress
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
ms.openlocfilehash: 6bbf8366054c58543444a4b710a687198f365e6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617185"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="ad4b5-102">Função GetRealProcAddress</span><span class="sxs-lookup"><span data-stu-id="ad4b5-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="ad4b5-103">Obtém o endereço da função especificada que é exportada da versão mais recente instalada do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="ad4b5-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad4b5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad4b5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad4b5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad4b5-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="ad4b5-107">no O nome da função.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="ad4b5-108">fora O local que recebe um ponteiro para o endereço da função.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad4b5-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ad4b5-109">Return Value</span></span>  
 <span data-ttu-id="ad4b5-110">Esse método retorna códigos de erro padrão de Component Object Model (COM), conforme definido no WinError. h, além dos valores a seguir definidos em CorError. h.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="ad4b5-111">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="ad4b5-111">Return code</span></span>|<span data-ttu-id="ad4b5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad4b5-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ad4b5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad4b5-113">S_OK</span></span>|<span data-ttu-id="ad4b5-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ad4b5-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ad4b5-115">E_POINTER</span></span>|<span data-ttu-id="ad4b5-116">`ppv` não é válido.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="ad4b5-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="ad4b5-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="ad4b5-118">A função não é exportada do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad4b5-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad4b5-119">Requirements</span></span>  
 <span data-ttu-id="ad4b5-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad4b5-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ad4b5-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad4b5-122">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ad4b5-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad4b5-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad4b5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad4b5-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="ad4b5-124">See also</span></span>

- [<span data-ttu-id="ad4b5-125">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="ad4b5-125">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
