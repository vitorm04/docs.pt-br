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
ms.openlocfilehash: f60f159ab4770023cee7123b39109040243e1ccd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136976"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="f784a-102">\_função CorDllMain</span><span class="sxs-lookup"><span data-stu-id="f784a-102">\_CorDllMain Function</span></span>

<span data-ttu-id="f784a-103">Inicializa o Common Language Runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly de DLL e começa a execução.</span><span class="sxs-lookup"><span data-stu-id="f784a-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f784a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f784a-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f784a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f784a-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="f784a-106">no O identificador de instância do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="f784a-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="f784a-107">no Indica por que a função de ponto de entrada de DLL está sendo chamada.</span><span class="sxs-lookup"><span data-stu-id="f784a-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="f784a-108">Esse parâmetro pode ser um dos seguintes valores: DLL\_PROCESS_ATTACH, DLL\_THREAD\_anexar, DLL\_THREAD\_ATTACH ou DLL\_processo\_desanexar.</span><span class="sxs-lookup"><span data-stu-id="f784a-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="f784a-109">Para obter descrições desses valores, consulte a documentação do `DllMain` no Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="f784a-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="f784a-110">no Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="f784a-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f784a-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f784a-111">Return Value</span></span>  
 <span data-ttu-id="f784a-112">Esse método retorna `true` para êxito e `false` se ocorrer um erro.</span><span class="sxs-lookup"><span data-stu-id="f784a-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f784a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f784a-113">Remarks</span></span>  
 <span data-ttu-id="f784a-114">Essa função é chamada pelo carregador do sistema operacional para assemblies DLL.</span><span class="sxs-lookup"><span data-stu-id="f784a-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="f784a-115">Para assemblies executáveis, o carregador chama a função [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f784a-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="f784a-116">O carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo DLL.</span><span class="sxs-lookup"><span data-stu-id="f784a-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="f784a-117">A função `_CorDllMain` é chamada diretamente pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f784a-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="f784a-118">Para obter informações adicionais, consulte a seção comentários no tópico [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f784a-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f784a-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f784a-119">Requirements</span></span>  

 <span data-ttu-id="f784a-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f784a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f784a-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f784a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f784a-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f784a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f784a-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f784a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f784a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f784a-124">See also</span></span>

- [<span data-ttu-id="f784a-125">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="f784a-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
