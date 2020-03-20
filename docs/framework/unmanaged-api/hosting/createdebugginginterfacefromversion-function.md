---
title: Função CreateDebuggingInterfaceFromVersion
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176442"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="26976-102">Função CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="26976-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="26976-103">Cria um objeto [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) com base nas informações da versão especificada.</span><span class="sxs-lookup"><span data-stu-id="26976-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="26976-104">Esta função está obsoleta no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="26976-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="26976-105">Em vez disso, para obter uma interface para o tempo de execução de idioma comum (CLR) 2.0, use o método [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) e especifique o identificador de classe CLSID_CLRDebuggingLegacy e o identificador de interface IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="26976-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="26976-106">Para obter uma interface para CLR 4 ou posterior, ligue para a função [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) e especifique o identificador de classe CLSID_CLRDebugging e o identificador de interface IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="26976-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26976-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26976-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26976-108">parâmetros</span><span class="sxs-lookup"><span data-stu-id="26976-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="26976-109">[em] A versão `ICorDebug` disso é esperada pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="26976-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="26976-110">Consulte a [enumeração CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) para obter valores válidos.</span><span class="sxs-lookup"><span data-stu-id="26976-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="26976-111">[em] A versão em tempo de execução do idioma comum associada ao aplicativo ou processo a ser depurado.</span><span class="sxs-lookup"><span data-stu-id="26976-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="26976-112">Consulte o método [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) para obter informações sobre como recuperar esse valor.</span><span class="sxs-lookup"><span data-stu-id="26976-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="26976-113">[fora] O local que recebe `ICorDebug` um ponteiro para o objeto.</span><span class="sxs-lookup"><span data-stu-id="26976-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26976-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="26976-114">Return Value</span></span>  
 <span data-ttu-id="26976-115">Este método retorna códigos de erro COM padrão conforme definido no arquivo WinError.h, além dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="26976-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="26976-116">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="26976-116">Return code</span></span>|<span data-ttu-id="26976-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="26976-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="26976-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="26976-118">S_OK</span></span>|<span data-ttu-id="26976-119">O método foi concluído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="26976-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="26976-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="26976-120">E_INVALIDARG</span></span>|<span data-ttu-id="26976-121">`szDebuggeeVersion`ou `ppCordb` é nulo, ou a seqüência de versão está incorreta.</span><span class="sxs-lookup"><span data-stu-id="26976-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26976-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="26976-122">Remarks</span></span>  
 <span data-ttu-id="26976-123">O `szDebuggeeVersion` parâmetro mapeia a versão correspondente de MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="26976-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26976-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26976-124">Requirements</span></span>  
 <span data-ttu-id="26976-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26976-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26976-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26976-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26976-127">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="26976-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26976-128">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26976-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26976-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="26976-129">See also</span></span>

- [<span data-ttu-id="26976-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="26976-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
