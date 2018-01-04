---
title: "Função CreateClassEnumWmi (referência de API não gerenciada)"
description: "A função CreateClassEnumWmi retorna um enumerador para todas as classes que atendem a critérios especificados."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CreateClassEnumWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CreateClassEnumWmi
helpviewer_keywords: CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2058bad61af79244d211afb6a7661ca1642db070
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="9ab9d-103">Função CreateClassEnumWmi</span><span class="sxs-lookup"><span data-stu-id="9ab9d-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="9ab9d-104">Retorna um enumerador para todas as classes que atendem aos critérios de seleção especificada.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9ab9d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ab9d-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="9ab9d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ab9d-106">Parameters</span></span>

`strSuperclass`    
<span data-ttu-id="9ab9d-107">[in] Se não `null` ou em branco, especifica o nome de uma classe pai; o enumerador retorna apenas as subclasses dessa classe.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="9ab9d-108">Se for `null` ou em branco e `lFlags` é WBEM_FLAG_SHALLOW, retorna apenas classes de nível superior (classes com nenhuma classe pai).</span><span class="sxs-lookup"><span data-stu-id="9ab9d-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="9ab9d-109">Se for `null` ou em branco e `lFlags` é `WBEM_FLAG_DEEP`, retorna todas as classes no namespace.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`   
<span data-ttu-id="9ab9d-110">[in] Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="9ab9d-111">Os seguintes valores são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="9ab9d-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="9ab9d-112">Constante</span><span class="sxs-lookup"><span data-stu-id="9ab9d-112">Constant</span></span>  |<span data-ttu-id="9ab9d-113">Valor</span><span class="sxs-lookup"><span data-stu-id="9ab9d-113">Value</span></span>  |<span data-ttu-id="9ab9d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ab9d-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="9ab9d-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="9ab9d-115">0x20000</span></span> | <span data-ttu-id="9ab9d-116">Se o conjunto, a função recupera os qualificadores aperfeiçoados armazenados no namespace localizado da localidade da conexão atual.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="9ab9d-117">Se não for definido, a função recupera somente os qualificadores armazenados no namespace de imediato.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="9ab9d-118">0</span><span class="sxs-lookup"><span data-stu-id="9ab9d-118">0</span></span> | <span data-ttu-id="9ab9d-119">A enumeração inclui todas as subclasses da hierarquia, mas não essa classe.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="9ab9d-120">1</span><span class="sxs-lookup"><span data-stu-id="9ab9d-120">1</span></span> | <span data-ttu-id="9ab9d-121">A enumeração inclui somente puras instâncias dessa classe e exclui todas as instâncias das subclasses que fornecem a propriedade não foi encontrada nesta classe.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="9ab9d-122">0x10</span><span class="sxs-lookup"><span data-stu-id="9ab9d-122">0x10</span></span> | <span data-ttu-id="9ab9d-123">O sinalizador faz com que uma chamada semi-síncrona.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="9ab9d-124">0x20</span><span class="sxs-lookup"><span data-stu-id="9ab9d-124">0x20</span></span> | <span data-ttu-id="9ab9d-125">A função retorna um enumerador de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="9ab9d-126">Normalmente, os enumeradores de somente avanço são mais rápidos e usam menos memória do que os enumeradores convencionais, mas não permitem chamadas para [Clone](clone.md).</span><span class="sxs-lookup"><span data-stu-id="9ab9d-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="9ab9d-127">0</span><span class="sxs-lookup"><span data-stu-id="9ab9d-127">0</span></span> | <span data-ttu-id="9ab9d-128">WMI retém ponteiros para objetos de enumration até que eles sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-128">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="9ab9d-129">Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="9ab9d-130">[in] Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="9ab9d-131">Caso contrário, é um ponteiro para um [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instância pode ser usada pelo provedor que fornece as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-131">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="9ab9d-132">[out] Recebe o ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="9ab9d-133">[in] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-133">[in] The authorization level.</span></span>

<span data-ttu-id="9ab9d-134">`impLevel`[in] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-134">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="9ab9d-135">[in] Um ponteiro para um [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objeto que representa o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-135">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="9ab9d-136">[in] O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-136">[in] The user name.</span></span> <span data-ttu-id="9ab9d-137">Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="9ab9d-138">[in] A senha.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-138">[in] The password.</span></span> <span data-ttu-id="9ab9d-139">Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="9ab9d-140">[in] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-140">[in] The domain name of the user.</span></span> <span data-ttu-id="9ab9d-141">Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ab9d-142">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9ab9d-142">Return value</span></span>

<span data-ttu-id="9ab9d-143">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="9ab9d-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9ab9d-144">Constante</span><span class="sxs-lookup"><span data-stu-id="9ab9d-144">Constant</span></span>  |<span data-ttu-id="9ab9d-145">Valor</span><span class="sxs-lookup"><span data-stu-id="9ab9d-145">Value</span></span>  |<span data-ttu-id="9ab9d-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ab9d-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="9ab9d-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="9ab9d-147">0x80041003</span></span> | <span data-ttu-id="9ab9d-148">O usuário não tem permissão para exibir um ou mais das classes que a função pode retornar.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="9ab9d-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9ab9d-149">0x80041001</span></span> | <span data-ttu-id="9ab9d-150">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="9ab9d-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="9ab9d-151">0x80041010</span></span> | <span data-ttu-id="9ab9d-152">`strSuperClass` não existe.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9ab9d-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9ab9d-153">0x80041008</span></span> | <span data-ttu-id="9ab9d-154">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9ab9d-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9ab9d-155">0x80041006</span></span> | <span data-ttu-id="9ab9d-156">Não há memória suficiente está disponível para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="9ab9d-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="9ab9d-157">0x80041033</span></span> | <span data-ttu-id="9ab9d-158">WMI foi provavelmente interrompido e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="9ab9d-159">Chamar [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="9ab9d-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="9ab9d-160">0x80041015</span></span> | <span data-ttu-id="9ab9d-161">O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9ab9d-162">0</span><span class="sxs-lookup"><span data-stu-id="9ab9d-162">0</span></span> | <span data-ttu-id="9ab9d-163">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9ab9d-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ab9d-164">Remarks</span></span>

<span data-ttu-id="9ab9d-165">Essa função encapsula uma chamada para o [Createclassenum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-165">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="9ab9d-166">Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="9ab9d-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ab9d-167">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ab9d-167">Requirements</span></span>  
 <span data-ttu-id="9ab9d-168">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ab9d-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ab9d-169">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9ab9d-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9ab9d-170">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9ab9d-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab9d-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ab9d-171">See also</span></span>  
[<span data-ttu-id="9ab9d-172">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="9ab9d-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
