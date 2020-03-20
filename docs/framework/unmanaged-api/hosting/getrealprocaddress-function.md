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
ms.openlocfilehash: 4c914e00987053b1c1e9e00bf8e54632175e1de8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178170"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="a29e3-102">Função GetRealProcAddress</span><span class="sxs-lookup"><span data-stu-id="a29e3-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="a29e3-103">Obtém o endereço da função especificada que é exportada a partir da versão mais recente instalada do tempo de execução do idioma comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="a29e3-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="a29e3-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="a29e3-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29e3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a29e3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a29e3-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="a29e3-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="a29e3-107">[em] O nome da função.</span><span class="sxs-lookup"><span data-stu-id="a29e3-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a29e3-108">[fora] O local que recebe um ponteiro para o endereço da função.</span><span class="sxs-lookup"><span data-stu-id="a29e3-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a29e3-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a29e3-109">Return Value</span></span>  
 <span data-ttu-id="a29e3-110">Este método retorna códigos de erro com o Modelo de Objeto Componente padrão (COM), conforme definido em WinError.h, além dos seguintes valores definidos em CorError.h.</span><span class="sxs-lookup"><span data-stu-id="a29e3-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="a29e3-111">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="a29e3-111">Return code</span></span>|<span data-ttu-id="a29e3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a29e3-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a29e3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a29e3-113">S_OK</span></span>|<span data-ttu-id="a29e3-114">O método foi concluído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="a29e3-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="a29e3-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a29e3-115">E_POINTER</span></span>|<span data-ttu-id="a29e3-116">`ppv` não é válido.</span><span class="sxs-lookup"><span data-stu-id="a29e3-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="a29e3-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="a29e3-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="a29e3-118">A função não é exportada a partir do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a29e3-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a29e3-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a29e3-119">Requirements</span></span>  
 <span data-ttu-id="a29e3-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a29e3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a29e3-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a29e3-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a29e3-122">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a29e3-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a29e3-123">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a29e3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29e3-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="a29e3-124">See also</span></span>

- [<span data-ttu-id="a29e3-125">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="a29e3-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
