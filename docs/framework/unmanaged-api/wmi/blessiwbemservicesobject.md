---
title: Função BlessIWbemServicesObject (referência de API não gerenciada)
description: A função BlessIWbemServicesObject indica se as credenciais de usuário permitirem o acesso a um objeto IWbemServices
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a561c5af868968624ee9ee81050d87b17c4591be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624412"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="d60fe-103">Função BlessIWbemServicesObject</span><span class="sxs-lookup"><span data-stu-id="d60fe-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="d60fe-104">Indica se as credenciais de usuário permitirem o acesso a determinado [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto.</span><span class="sxs-lookup"><span data-stu-id="d60fe-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d60fe-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d60fe-105">Syntax</span></span>  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="d60fe-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d60fe-106">Parameters</span></span>

`pIWbemServices`  
<span data-ttu-id="d60fe-107">[in] Um ponteiro para um objeto de serviço do WMI.</span><span class="sxs-lookup"><span data-stu-id="d60fe-107">[in] A pointer to a WMI service object.</span></span>

`strUser`  
<span data-ttu-id="d60fe-108">[in] O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="d60fe-108">[in] The user name.</span></span>

`strPassword`  
<span data-ttu-id="d60fe-109">[in] A senha associada `strUser`.</span><span class="sxs-lookup"><span data-stu-id="d60fe-109">[in] The password associated with `strUser`.</span></span>

<span data-ttu-id="d60fe-110">`strAuthority` [in] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="d60fe-110">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="d60fe-111">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="d60fe-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="d60fe-112">`impLevel` [in] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="d60fe-112">`impLevel` [in] The impersonation level.</span></span>

<span data-ttu-id="d60fe-113">`authnLevel` [in] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="d60fe-113">`authnLevel` [in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="d60fe-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d60fe-114">Return value</span></span>

<span data-ttu-id="d60fe-115">Os seguintes valores retornados por essa função são definidos na *Winerror. H* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="d60fe-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d60fe-116">Constante</span><span class="sxs-lookup"><span data-stu-id="d60fe-116">Constant</span></span>  |<span data-ttu-id="d60fe-117">Valor</span><span class="sxs-lookup"><span data-stu-id="d60fe-117">Value</span></span>  |<span data-ttu-id="d60fe-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d60fe-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="d60fe-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="d60fe-119">0x80070057</span></span> | <span data-ttu-id="d60fe-120">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="d60fe-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="d60fe-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="d60fe-121">0x80004003</span></span> | <span data-ttu-id="d60fe-122">`pIWbemServices` é `null`.</span><span class="sxs-lookup"><span data-stu-id="d60fe-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="d60fe-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="d60fe-123">0x80000008</span></span> | <span data-ttu-id="d60fe-124">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="d60fe-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="d60fe-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="d60fe-125">0x80000002</span></span> | <span data-ttu-id="d60fe-126">Memória disponível é insuficiente para executar a operação.</span><span class="sxs-lookup"><span data-stu-id="d60fe-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="d60fe-127">0</span><span class="sxs-lookup"><span data-stu-id="d60fe-127">0</span></span> | <span data-ttu-id="d60fe-128">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d60fe-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="d60fe-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d60fe-129">Requirements</span></span>  
 <span data-ttu-id="d60fe-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d60fe-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d60fe-131">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d60fe-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d60fe-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d60fe-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d60fe-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d60fe-133">See also</span></span>
- [<span data-ttu-id="d60fe-134">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="d60fe-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
