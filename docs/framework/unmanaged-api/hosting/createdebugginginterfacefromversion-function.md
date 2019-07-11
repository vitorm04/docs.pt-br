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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe34ffded73e8305e4ade3bb9b402b1d8e1bcc49
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764679"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="434fa-102">Função CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="434fa-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="434fa-103">Cria uma [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objeto com base nas informações de versão especificadas.</span><span class="sxs-lookup"><span data-stu-id="434fa-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="434fa-104">Essa função está obsoleta no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="434fa-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="434fa-105">Em vez disso, para obter uma interface para o common language runtime (CLR) 2.0, use o [iclrruntimeinfo:: Getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) método e especifique o identificador de classe CLSID_CLRDebuggingLegacy e o identificador de interface IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="434fa-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="434fa-106">Para obter uma interface CLR 4 ou posterior, chame o [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) de função e especifique o identificador de classe CLSID_CLRDebugging e o identificador de interface IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="434fa-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="434fa-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="434fa-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="434fa-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="434fa-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="434fa-109">[in] A versão do `ICorDebug` que é esperado pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="434fa-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="434fa-110">Consulte a [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeração para os valores válidos.</span><span class="sxs-lookup"><span data-stu-id="434fa-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="434fa-111">[in] A versão common language runtime associado com o aplicativo ou processo a ser depurado.</span><span class="sxs-lookup"><span data-stu-id="434fa-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="434fa-112">Consulte a [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) método para obter informações sobre como recuperar esse valor.</span><span class="sxs-lookup"><span data-stu-id="434fa-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="434fa-113">[out] O local que recebe um ponteiro para o `ICorDebug` objeto.</span><span class="sxs-lookup"><span data-stu-id="434fa-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="434fa-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="434fa-114">Return Value</span></span>  
 <span data-ttu-id="434fa-115">Esse método retorna códigos de erro padrão COM conforme definido no arquivo Winerror h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="434fa-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="434fa-116">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="434fa-116">Return code</span></span>|<span data-ttu-id="434fa-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="434fa-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="434fa-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="434fa-118">S_OK</span></span>|<span data-ttu-id="434fa-119">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="434fa-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="434fa-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="434fa-120">E_INVALIDARG</span></span>|<span data-ttu-id="434fa-121">`szDebuggeeVersion` ou `ppCordb` é nulo ou a versão de cadeia de caracteres está incorreta.</span><span class="sxs-lookup"><span data-stu-id="434fa-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="434fa-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="434fa-122">Remarks</span></span>  
 <span data-ttu-id="434fa-123">O `szDebuggeeVersion` parâmetro é mapeado para a versão correspondente do mscordbi.</span><span class="sxs-lookup"><span data-stu-id="434fa-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="434fa-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="434fa-124">Requirements</span></span>  
 <span data-ttu-id="434fa-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="434fa-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="434fa-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="434fa-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="434fa-127">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="434fa-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="434fa-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="434fa-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434fa-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="434fa-129">See also</span></span>

- [<span data-ttu-id="434fa-130">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="434fa-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
