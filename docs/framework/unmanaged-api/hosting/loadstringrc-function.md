---
title: Função LoadStringRC
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176234"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="73de8-102">Função LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="73de8-102">LoadStringRC Function</span></span>
<span data-ttu-id="73de8-103">Traduz um valor HRESULT em uma mensagem de erro usando a cultura padrão do segmento atual.</span><span class="sxs-lookup"><span data-stu-id="73de8-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="73de8-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="73de8-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73de8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73de8-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73de8-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="73de8-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="73de8-107">[em] Um HRESULT.</span><span class="sxs-lookup"><span data-stu-id="73de8-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="73de8-108">[fora] Um buffer que contém a mensagem de erro após a conclusão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="73de8-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="73de8-109">[em] O tamanho do buffer de mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="73de8-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="73de8-110">[em] Ignorado.</span><span class="sxs-lookup"><span data-stu-id="73de8-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73de8-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="73de8-111">Return Value</span></span>  
 <span data-ttu-id="73de8-112">Este método retorna códigos de erro com (Component Object Model, modelo de objeto componente padrão), conforme definido em WinError.h, além dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="73de8-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="73de8-113">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="73de8-113">Return code</span></span>|<span data-ttu-id="73de8-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="73de8-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="73de8-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="73de8-115">S_OK</span></span>|<span data-ttu-id="73de8-116">O método foi concluído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="73de8-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="73de8-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="73de8-117">E_INVALIDARG</span></span>|<span data-ttu-id="73de8-118">`szBuffer`é nulo ou `iMax` é zero (0).</span><span class="sxs-lookup"><span data-stu-id="73de8-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73de8-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="73de8-119">Remarks</span></span>  
 <span data-ttu-id="73de8-120">Se o método não `szBuffer` for concluído com sucesso, contém uma seqüência vazia.</span><span class="sxs-lookup"><span data-stu-id="73de8-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73de8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73de8-121">Requirements</span></span>  
 <span data-ttu-id="73de8-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73de8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73de8-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="73de8-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73de8-124">**Biblioteca:** MSCorEE.dll e Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="73de8-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="73de8-125">Use o MSCorEE.dll em vez de Mscorwks.dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="73de8-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="73de8-126">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73de8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73de8-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="73de8-127">See also</span></span>

- [<span data-ttu-id="73de8-128">Função LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="73de8-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="73de8-129">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="73de8-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
