---
title: Função BlessIWbemServices (referência de API não gerenciada)
description: A função BlessIWbemServices indica se as credenciais do usuário permitem acesso a uma classe IWbemServices.
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
ms.openlocfilehash: 4b15af840cc00b3ec261604db4f3625c6b975d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176858"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="07d19-103">Função BlessIWbemServices</span><span class="sxs-lookup"><span data-stu-id="07d19-103">BlessIWbemServices function</span></span>
<span data-ttu-id="07d19-104">Indica se as credenciais do usuário permitem acesso à classe [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) especificada.</span><span class="sxs-lookup"><span data-stu-id="07d19-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="07d19-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07d19-105">Syntax</span></span>  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="07d19-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="07d19-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="07d19-107">[em] Um ponteiro para o objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) para o qual as permissões são necessárias.</span><span class="sxs-lookup"><span data-stu-id="07d19-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="07d19-108">[em] O nome do usuário.</span><span class="sxs-lookup"><span data-stu-id="07d19-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="07d19-109">[em] A senha `strUser`associada a .</span><span class="sxs-lookup"><span data-stu-id="07d19-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="07d19-110">[em] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="07d19-110">[in] The domain name of the user.</span></span> <span data-ttu-id="07d19-111">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="07d19-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="07d19-112">[em] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="07d19-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="07d19-113">[em] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="07d19-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="07d19-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="07d19-114">Return value</span></span>

<span data-ttu-id="07d19-115">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WinError.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="07d19-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="07d19-116">Constante</span><span class="sxs-lookup"><span data-stu-id="07d19-116">Constant</span></span>  |<span data-ttu-id="07d19-117">Valor</span><span class="sxs-lookup"><span data-stu-id="07d19-117">Value</span></span>  |<span data-ttu-id="07d19-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="07d19-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="07d19-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="07d19-119">0x80070057</span></span> | <span data-ttu-id="07d19-120">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="07d19-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="07d19-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="07d19-121">0x80004003</span></span> | <span data-ttu-id="07d19-122">`pIWbemServices` é `null`.</span><span class="sxs-lookup"><span data-stu-id="07d19-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="07d19-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="07d19-123">0x80000008</span></span> | <span data-ttu-id="07d19-124">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="07d19-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="07d19-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="07d19-125">0x80000002</span></span> | <span data-ttu-id="07d19-126">A memória insuficiente está disponível para realizar a operação.</span><span class="sxs-lookup"><span data-stu-id="07d19-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="07d19-127">0</span><span class="sxs-lookup"><span data-stu-id="07d19-127">0</span></span> | <span data-ttu-id="07d19-128">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="07d19-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="07d19-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07d19-129">Requirements</span></span>  

 <span data-ttu-id="07d19-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07d19-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07d19-131">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="07d19-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="07d19-132">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="07d19-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d19-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="07d19-133">See also</span></span>

- [<span data-ttu-id="07d19-134">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="07d19-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
