---
title: Função CloneEnumWbemClassObject (referência de API não gerenciada)
description: A função CloneEnumWbemClassObject faz uma cópia lógica de um enumerador.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605314f94fd82d2a2cd7be105dde9e273f607bc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798702"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="868b2-103">Função CloneEnumWbemClassObject</span><span class="sxs-lookup"><span data-stu-id="868b2-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="868b2-104">Faz uma cópia lógica de um enumerador, mantendo sua posição atual em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="868b2-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="868b2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="868b2-105">Syntax</span></span>

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```

## <a name="parameters"></a><span data-ttu-id="868b2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="868b2-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="868b2-107">fora Recebe um ponteiro para um novo [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="868b2-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="868b2-108">no O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="868b2-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="868b2-109">no O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="868b2-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="868b2-110">fora Um ponteiro para a instância de [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) a ser clonada.</span><span class="sxs-lookup"><span data-stu-id="868b2-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="868b2-111">no O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="868b2-111">[in] The user name.</span></span> <span data-ttu-id="868b2-112">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="868b2-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="868b2-113">no A senha.</span><span class="sxs-lookup"><span data-stu-id="868b2-113">[in] The password.</span></span> <span data-ttu-id="868b2-114">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="868b2-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="868b2-115">`strAuthority`\ [in] o nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="868b2-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="868b2-116">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="868b2-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="868b2-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="868b2-117">Return value</span></span>

<span data-ttu-id="868b2-118">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="868b2-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="868b2-119">Constante</span><span class="sxs-lookup"><span data-stu-id="868b2-119">Constant</span></span>  |<span data-ttu-id="868b2-120">Valor</span><span class="sxs-lookup"><span data-stu-id="868b2-120">Value</span></span>  |<span data-ttu-id="868b2-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="868b2-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="868b2-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="868b2-122">0x80041001</span></span> | <span data-ttu-id="868b2-123">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="868b2-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="868b2-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="868b2-124">0x80041008</span></span> | <span data-ttu-id="868b2-125">Um parâmetro é inválido.</span><span class="sxs-lookup"><span data-stu-id="868b2-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="868b2-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="868b2-126">0x80041006</span></span> | <span data-ttu-id="868b2-127">Não há memória suficiente disponível conclua a operação.</span><span class="sxs-lookup"><span data-stu-id="868b2-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="868b2-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="868b2-128">0x80041015</span></span> | <span data-ttu-id="868b2-129">O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="868b2-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="868b2-130">0</span><span class="sxs-lookup"><span data-stu-id="868b2-130">0</span></span> | <span data-ttu-id="868b2-131">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="868b2-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="868b2-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="868b2-132">Remarks</span></span>

<span data-ttu-id="868b2-133">Essa função encapsula uma chamada para o método [IEnumWbemClassObject:: clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="868b2-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="868b2-134">Esse método faz apenas uma cópia "melhor esforço".</span><span class="sxs-lookup"><span data-stu-id="868b2-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="868b2-135">Devido à natureza dinâmica de muitos objetos CIM, é possível que o novo enumerador não enumere o mesmo conjunto de objetos que o enumerador de origem.</span><span class="sxs-lookup"><span data-stu-id="868b2-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="868b2-136">Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="868b2-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="868b2-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="868b2-137">Example</span></span>

<span data-ttu-id="868b2-138">Para obter um exemplo, consulte o método [IEnumWbemClassObject:: clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="868b2-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="868b2-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="868b2-139">Requirements</span></span>
 <span data-ttu-id="868b2-140">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="868b2-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="868b2-141">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="868b2-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="868b2-142">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="868b2-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="868b2-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="868b2-143">See also</span></span>

- [<span data-ttu-id="868b2-144">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="868b2-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
