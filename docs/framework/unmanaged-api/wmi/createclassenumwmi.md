---
title: Função CreateClassEnumWmi (referência de API não gerenciada)
description: A função CreateClassEnumWmi retorna um enumerador para todas as classes que atendem aos critérios especificados.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a696a6f02f6d3a5afbcb45e5566e4b667739e2c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798732"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="77c1c-103">Função CreateClassEnumWmi</span><span class="sxs-lookup"><span data-stu-id="77c1c-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="77c1c-104">Retorna um enumerador para todas as classes que satisfaçam os critérios de seleção especificados.</span><span class="sxs-lookup"><span data-stu-id="77c1c-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="77c1c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77c1c-105">Syntax</span></span>

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="77c1c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77c1c-106">Parameters</span></span>

`strSuperclass`\
<span data-ttu-id="77c1c-107">no Se não `null` estiver ou em branco, especifica o nome de uma classe pai; o enumerador retorna apenas subclasses dessa classe.</span><span class="sxs-lookup"><span data-stu-id="77c1c-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="77c1c-108">Se estiver `null` ou em branco e `lFlags` for WBEM_FLAG_SHALLOW, retornará somente classes de nível superior (classes sem classe pai).</span><span class="sxs-lookup"><span data-stu-id="77c1c-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="77c1c-109">Se estiver `null` ou em branco e `lFlags` for `WBEM_FLAG_DEEP`, retorna todas as classes no namespace.</span><span class="sxs-lookup"><span data-stu-id="77c1c-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`\
<span data-ttu-id="77c1c-110">no Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="77c1c-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="77c1c-111">Os valores a seguir são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="77c1c-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="77c1c-112">Constante</span><span class="sxs-lookup"><span data-stu-id="77c1c-112">Constant</span></span>  |<span data-ttu-id="77c1c-113">Valor</span><span class="sxs-lookup"><span data-stu-id="77c1c-113">Value</span></span>  |<span data-ttu-id="77c1c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="77c1c-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="77c1c-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="77c1c-115">0x20000</span></span> | <span data-ttu-id="77c1c-116">Se definido, a função recupera os qualificadores corrigidos armazenados no namespace localizado da localidade da conexão atual.</span><span class="sxs-lookup"><span data-stu-id="77c1c-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="77c1c-117">Se não for definido, a função recuperará somente os qualificadores armazenados no namespace imediato.</span><span class="sxs-lookup"><span data-stu-id="77c1c-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="77c1c-118">0</span><span class="sxs-lookup"><span data-stu-id="77c1c-118">0</span></span> | <span data-ttu-id="77c1c-119">A enumeração inclui todas as subclasses na hierarquia, mas não essa classe.</span><span class="sxs-lookup"><span data-stu-id="77c1c-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="77c1c-120">1</span><span class="sxs-lookup"><span data-stu-id="77c1c-120">1</span></span> | <span data-ttu-id="77c1c-121">A enumeração inclui apenas instâncias puras dessa classe e exclui todas as instâncias de subclasses que fornecem propriedades não encontradas nesta classe.</span><span class="sxs-lookup"><span data-stu-id="77c1c-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="77c1c-122">0x10</span><span class="sxs-lookup"><span data-stu-id="77c1c-122">0x10</span></span> | <span data-ttu-id="77c1c-123">O sinalizador causa uma chamada de semisynchronous.</span><span class="sxs-lookup"><span data-stu-id="77c1c-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="77c1c-124">0x20</span><span class="sxs-lookup"><span data-stu-id="77c1c-124">0x20</span></span> | <span data-ttu-id="77c1c-125">A função retorna um enumerador somente encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="77c1c-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="77c1c-126">Normalmente, enumeradores somente de encaminhamento são mais rápidos e usam menos memória do que enumeradores convencionais, mas não permitem que as chamadas [clonem](clone.md).</span><span class="sxs-lookup"><span data-stu-id="77c1c-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="77c1c-127">0</span><span class="sxs-lookup"><span data-stu-id="77c1c-127">0</span></span> | <span data-ttu-id="77c1c-128">O WMI retém ponteiros para objetos na enumeração até que sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="77c1c-128">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="77c1c-129">Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para obter o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="77c1c-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="77c1c-130">no Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="77c1c-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="77c1c-131">Caso contrário, é um ponteiro para uma instância de [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) que pode ser usada pelo provedor que está fornecendo as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="77c1c-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="77c1c-132">fora Recebe o ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="77c1c-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="77c1c-133">no O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="77c1c-133">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="77c1c-134">no O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="77c1c-134">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="77c1c-135">no Um ponteiro para um objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) que representa o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="77c1c-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="77c1c-136">no O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="77c1c-136">[in] The user name.</span></span> <span data-ttu-id="77c1c-137">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="77c1c-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="77c1c-138">no A senha.</span><span class="sxs-lookup"><span data-stu-id="77c1c-138">[in] The password.</span></span> <span data-ttu-id="77c1c-139">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="77c1c-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="77c1c-140">no O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="77c1c-140">[in] The domain name of the user.</span></span> <span data-ttu-id="77c1c-141">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="77c1c-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="77c1c-142">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="77c1c-142">Return value</span></span>

<span data-ttu-id="77c1c-143">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="77c1c-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="77c1c-144">Constante</span><span class="sxs-lookup"><span data-stu-id="77c1c-144">Constant</span></span>  |<span data-ttu-id="77c1c-145">Valor</span><span class="sxs-lookup"><span data-stu-id="77c1c-145">Value</span></span>  |<span data-ttu-id="77c1c-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="77c1c-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="77c1c-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="77c1c-147">0x80041003</span></span> | <span data-ttu-id="77c1c-148">O usuário não tem permissão para exibir uma ou mais das classes que a função pode retornar.</span><span class="sxs-lookup"><span data-stu-id="77c1c-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="77c1c-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="77c1c-149">0x80041001</span></span> | <span data-ttu-id="77c1c-150">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="77c1c-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="77c1c-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="77c1c-151">0x80041010</span></span> | <span data-ttu-id="77c1c-152">`strSuperClass` não existe.</span><span class="sxs-lookup"><span data-stu-id="77c1c-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="77c1c-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="77c1c-153">0x80041008</span></span> | <span data-ttu-id="77c1c-154">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="77c1c-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="77c1c-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="77c1c-155">0x80041006</span></span> | <span data-ttu-id="77c1c-156">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="77c1c-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="77c1c-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="77c1c-157">0x80041033</span></span> | <span data-ttu-id="77c1c-158">O WMI provavelmente foi interrompido e reiniciado.</span><span class="sxs-lookup"><span data-stu-id="77c1c-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="77c1c-159">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="77c1c-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="77c1c-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="77c1c-160">0x80041015</span></span> | <span data-ttu-id="77c1c-161">O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="77c1c-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="77c1c-162">0</span><span class="sxs-lookup"><span data-stu-id="77c1c-162">0</span></span> | <span data-ttu-id="77c1c-163">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="77c1c-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="77c1c-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="77c1c-164">Remarks</span></span>

<span data-ttu-id="77c1c-165">Essa função encapsula uma chamada para o método [IWbemServices:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) .</span><span class="sxs-lookup"><span data-stu-id="77c1c-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="77c1c-166">Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="77c1c-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="77c1c-167">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77c1c-167">Requirements</span></span>

<span data-ttu-id="77c1c-168">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77c1c-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="77c1c-169">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="77c1c-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="77c1c-170">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="77c1c-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="77c1c-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77c1c-171">See also</span></span>

- [<span data-ttu-id="77c1c-172">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="77c1c-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
