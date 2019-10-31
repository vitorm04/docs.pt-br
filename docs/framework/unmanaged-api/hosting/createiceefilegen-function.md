---
title: Função CreateICeeFileGen
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: de27851b4afc3eccad46531848c68723bff346d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136830"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="f12bb-102">Função CreateICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="f12bb-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="f12bb-103">Cria um objeto [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="f12bb-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="f12bb-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f12bb-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12bb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f12bb-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f12bb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f12bb-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="f12bb-107">fora Um ponteiro para o endereço de um novo objeto `ICeeFileGen`.</span><span class="sxs-lookup"><span data-stu-id="f12bb-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f12bb-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f12bb-108">Return Value</span></span>  
 <span data-ttu-id="f12bb-109">Esse método retorna códigos de erro COM padrão.</span><span class="sxs-lookup"><span data-stu-id="f12bb-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f12bb-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f12bb-110">Remarks</span></span>  
 <span data-ttu-id="f12bb-111">O objeto `ICeeFileGen` é usado para criar arquivos PE (executáveis portáteis) Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f12bb-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="f12bb-112">Chame a função [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) para destruir o objeto `ICeeFileGen` quando terminar.</span><span class="sxs-lookup"><span data-stu-id="f12bb-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f12bb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f12bb-113">Requirements</span></span>  
 <span data-ttu-id="f12bb-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12bb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12bb-115">**Cabeçalho:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="f12bb-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="f12bb-116">**Biblioteca:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="f12bb-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="f12bb-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12bb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12bb-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f12bb-118">See also</span></span>

- [<span data-ttu-id="f12bb-119">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="f12bb-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
