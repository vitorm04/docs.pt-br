---
title: Função LoadStringRCEx
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ec8e5dfc92a818bfc23c28f3058086c3bd1a8ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597938"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="7820f-102">Função LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="7820f-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="7820f-103">Converte um valor HRESULT a uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="7820f-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="7820f-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7820f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7820f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7820f-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7820f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7820f-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="7820f-107">[in] Um identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="7820f-107">[in] A culture identifier.</span></span> <span data-ttu-id="7820f-108">Passe -1 `lcid` para usar a cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="7820f-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="7820f-109">[in] Um HRESULT.</span><span class="sxs-lookup"><span data-stu-id="7820f-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="7820f-110">[out] Um buffer que contém a mensagem de erro após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="7820f-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="7820f-111">[in] O tamanho do buffer de mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="7820f-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="7820f-112">[in] Ignorado.</span><span class="sxs-lookup"><span data-stu-id="7820f-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="7820f-113">[out] Um ponteiro para o comprimento da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="7820f-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7820f-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7820f-114">Return Value</span></span>  
 <span data-ttu-id="7820f-115">Esse método retorna códigos de erro COM padrão, conforme definido em Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="7820f-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="7820f-116">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="7820f-116">Return code</span></span>|<span data-ttu-id="7820f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7820f-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7820f-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="7820f-118">S_OK</span></span>|<span data-ttu-id="7820f-119">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="7820f-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="7820f-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7820f-120">E_INVALIDARG</span></span>|<span data-ttu-id="7820f-121">`szBuffer` é nulo, ou `iMax` é zero (0).</span><span class="sxs-lookup"><span data-stu-id="7820f-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7820f-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="7820f-122">Remarks</span></span>  
 <span data-ttu-id="7820f-123">Se o método não for concluída com êxito, `szBuffer` contém uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="7820f-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7820f-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7820f-124">Requirements</span></span>  
 <span data-ttu-id="7820f-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7820f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7820f-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7820f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7820f-127">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7820f-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7820f-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7820f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7820f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7820f-129">See also</span></span>
- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7820f-130">Função LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="7820f-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="7820f-131">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="7820f-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
