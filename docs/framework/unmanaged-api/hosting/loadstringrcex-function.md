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
ms.openlocfilehash: 68332aee895f012bcf6ab6a72936c8dddc7f28a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122042"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="2965e-102">Função LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="2965e-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="2965e-103">Traduz um valor HRESULT para uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="2965e-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="2965e-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2965e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2965e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2965e-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2965e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2965e-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="2965e-107">no Um identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="2965e-107">[in] A culture identifier.</span></span> <span data-ttu-id="2965e-108">Pass-1 para `lcid` usar a cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="2965e-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="2965e-109">no Um HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2965e-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="2965e-110">fora Um buffer que contém a mensagem de erro após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="2965e-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="2965e-111">no O tamanho do buffer de mensagens de erro.</span><span class="sxs-lookup"><span data-stu-id="2965e-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="2965e-112">no Aceita.</span><span class="sxs-lookup"><span data-stu-id="2965e-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="2965e-113">fora Um ponteiro para o comprimento da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="2965e-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2965e-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2965e-114">Return Value</span></span>  
 <span data-ttu-id="2965e-115">Esse método retorna códigos de erro COM padrão, conforme definido no WinError. h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="2965e-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="2965e-116">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="2965e-116">Return code</span></span>|<span data-ttu-id="2965e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2965e-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2965e-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="2965e-118">S_OK</span></span>|<span data-ttu-id="2965e-119">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="2965e-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="2965e-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2965e-120">E_INVALIDARG</span></span>|<span data-ttu-id="2965e-121">`szBuffer` é nulo ou `iMax` é zero (0).</span><span class="sxs-lookup"><span data-stu-id="2965e-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2965e-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="2965e-122">Remarks</span></span>  
 <span data-ttu-id="2965e-123">Se o método não for concluído com êxito, `szBuffer` conterá uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="2965e-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2965e-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2965e-124">Requirements</span></span>  
 <span data-ttu-id="2965e-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2965e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2965e-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2965e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2965e-127">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2965e-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2965e-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2965e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2965e-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2965e-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2965e-130">Função LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="2965e-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="2965e-131">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="2965e-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
