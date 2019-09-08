---
title: Função BlessIWbemServices (referência de API não gerenciada)
description: A função BlessIWbemServices indica se as credenciais do usuário permitem o acesso a uma classe IWbemServices.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57ab5eb418b5f0a9175074c87837c7cac8936346
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799051"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="ecef1-103">Função BlessIWbemServices</span><span class="sxs-lookup"><span data-stu-id="ecef1-103">BlessIWbemServices function</span></span>
<span data-ttu-id="ecef1-104">Indica se as credenciais do usuário permitem o acesso à classe [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) especificada.</span><span class="sxs-lookup"><span data-stu-id="ecef1-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ecef1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecef1-105">Syntax</span></span>  
  
```  
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="ecef1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ecef1-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="ecef1-107">no Um ponteiro para o objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) para o qual são necessárias permissões.</span><span class="sxs-lookup"><span data-stu-id="ecef1-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="ecef1-108">no O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="ecef1-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="ecef1-109">no A senha associada `strUser`a.</span><span class="sxs-lookup"><span data-stu-id="ecef1-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="ecef1-110">no O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="ecef1-110">[in] The domain name of the user.</span></span> <span data-ttu-id="ecef1-111">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ecef1-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="ecef1-112">no O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="ecef1-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="ecef1-113">no O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="ecef1-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="ecef1-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ecef1-114">Return value</span></span>

<span data-ttu-id="ecef1-115">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *Winerror. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="ecef1-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ecef1-116">Constante</span><span class="sxs-lookup"><span data-stu-id="ecef1-116">Constant</span></span>  |<span data-ttu-id="ecef1-117">Valor</span><span class="sxs-lookup"><span data-stu-id="ecef1-117">Value</span></span>  |<span data-ttu-id="ecef1-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecef1-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="ecef1-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="ecef1-119">0x80070057</span></span> | <span data-ttu-id="ecef1-120">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="ecef1-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="ecef1-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="ecef1-121">0x80004003</span></span> | <span data-ttu-id="ecef1-122">`pIWbemServices` é `null`.</span><span class="sxs-lookup"><span data-stu-id="ecef1-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="ecef1-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="ecef1-123">0x80000008</span></span> | <span data-ttu-id="ecef1-124">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="ecef1-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="ecef1-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="ecef1-125">0x80000002</span></span> | <span data-ttu-id="ecef1-126">Memória insuficiente disponível para executar a operação.</span><span class="sxs-lookup"><span data-stu-id="ecef1-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="ecef1-127">0</span><span class="sxs-lookup"><span data-stu-id="ecef1-127">0</span></span> | <span data-ttu-id="ecef1-128">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ecef1-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="ecef1-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ecef1-129">Requirements</span></span>  

 <span data-ttu-id="ecef1-130">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecef1-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecef1-131">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ecef1-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ecef1-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ecef1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecef1-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecef1-133">See also</span></span>

- [<span data-ttu-id="ecef1-134">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="ecef1-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
