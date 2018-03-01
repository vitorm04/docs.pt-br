---
title: "Função _CorDllMain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 985f2284026054217671de767c316b1fba35c098
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordllmain-function"></a><span data-ttu-id="ae6ad-102">Função _CorDllMain</span><span class="sxs-lookup"><span data-stu-id="ae6ad-102">_CorDllMain Function</span></span>
<span data-ttu-id="ae6ad-103">Inicializa o common language runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho do CLR do assembly DLL e começa a ser executada.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae6ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae6ad-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae6ad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ae6ad-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="ae6ad-106">[in] O identificador de instância do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="ae6ad-107">[in] Indica o motivo pelo qual a função de ponto de entrada DLL está sendo chamada.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="ae6ad-108">Esse parâmetro pode ser um dos seguintes valores: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH ou DLL_PROCESS_DETACH.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-108">This parameter can be one of the following values: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH, or DLL_PROCESS_DETACH.</span></span> <span data-ttu-id="ae6ad-109">Para obter descrições desses valores, consulte o `DllMain` documentação no SDK da plataforma.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="ae6ad-110">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae6ad-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ae6ad-111">Return Value</span></span>  
 <span data-ttu-id="ae6ad-112">Este método retorna `true` para êxito e `false` se ocorrer um erro.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae6ad-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae6ad-113">Remarks</span></span>  
 <span data-ttu-id="ae6ad-114">Essa função é chamada pelo carregador do sistema operacional para os assemblies DLL.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="ae6ad-115">Para assemblies executável, o carregador chama o [CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-115">For executable assemblies, the loader calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="ae6ad-116">O carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo de DLL.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
 <span data-ttu-id="ae6ad-117">No Windows 98, Windows ME, Windows NT e Windows 2000, o `_CorDllMain` função é chamada indiretamente por meio de um fixupin carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-117">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorDllMain` function is called indirectly through a fixupin the operating system loader.</span></span> <span data-ttu-id="ae6ad-118">Em todas as outras versões do Windows, ele é chamado diretamente pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-118">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="ae6ad-119">Para obter mais informações, consulte a seção comentários a [CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="ae6ad-119">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae6ad-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae6ad-120">Requirements</span></span>  
 <span data-ttu-id="ae6ad-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae6ad-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae6ad-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ae6ad-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae6ad-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ae6ad-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ae6ad-124">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae6ad-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae6ad-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae6ad-125">See Also</span></span>  
 [<span data-ttu-id="ae6ad-126">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="ae6ad-126">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
