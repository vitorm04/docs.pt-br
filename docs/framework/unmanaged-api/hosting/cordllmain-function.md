---
title: Função _CorDllMain
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c509f475d5bf0105ece9791ee3e51d21c298a31f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666906"
---
# <a name="cordllmain-function"></a><span data-ttu-id="80fa2-102">\_Função CorDllMain</span><span class="sxs-lookup"><span data-stu-id="80fa2-102">\_CorDllMain Function</span></span>

<span data-ttu-id="80fa2-103">Inicializa o common language runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho do CLR do assembly da DLL e inicia a execução.</span><span class="sxs-lookup"><span data-stu-id="80fa2-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80fa2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80fa2-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80fa2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80fa2-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="80fa2-106">[in] O identificador da instância do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="80fa2-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="80fa2-107">[in] Indica por que a função de ponto de entrada DLL está sendo chamada.</span><span class="sxs-lookup"><span data-stu-id="80fa2-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="80fa2-108">Esse parâmetro pode ser um dos seguintes valores: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ANEXAR ou DLL\_processo\_DESANEXAR.</span><span class="sxs-lookup"><span data-stu-id="80fa2-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="80fa2-109">Para obter descrições desses valores, consulte o `DllMain` documentação no SDK da plataforma.</span><span class="sxs-lookup"><span data-stu-id="80fa2-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="80fa2-110">[in] Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="80fa2-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80fa2-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="80fa2-111">Return Value</span></span>  
 <span data-ttu-id="80fa2-112">Esse método retornará `true` para o sucesso e `false` se ocorrer um erro.</span><span class="sxs-lookup"><span data-stu-id="80fa2-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80fa2-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="80fa2-113">Remarks</span></span>  
 <span data-ttu-id="80fa2-114">Essa função é chamada pelo carregador do sistema operacional para os assemblies DLL.</span><span class="sxs-lookup"><span data-stu-id="80fa2-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="80fa2-115">Para assemblies executáveis, o carregador de chamadas a [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function em vez disso.</span><span class="sxs-lookup"><span data-stu-id="80fa2-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="80fa2-116">Carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo de DLL.</span><span class="sxs-lookup"><span data-stu-id="80fa2-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="80fa2-117">O `_CorDllMain` função é chamada diretamente pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="80fa2-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="80fa2-118">Para obter mais informações, consulte a seção comentários a [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="80fa2-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80fa2-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80fa2-119">Requirements</span></span>  

 <span data-ttu-id="80fa2-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80fa2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80fa2-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80fa2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80fa2-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="80fa2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80fa2-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80fa2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80fa2-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80fa2-124">See also</span></span>

- [<span data-ttu-id="80fa2-125">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="80fa2-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
