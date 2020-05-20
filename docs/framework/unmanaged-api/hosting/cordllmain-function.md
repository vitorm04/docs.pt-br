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
ms.openlocfilehash: 3b2322f708afed08172f87e843c225aa9c60d9d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616598"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="3cd77-102">\_Função CorDllMain</span><span class="sxs-lookup"><span data-stu-id="3cd77-102">\_CorDllMain Function</span></span>

<span data-ttu-id="3cd77-103">Inicializa o Common Language Runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly de DLL e começa a execução.</span><span class="sxs-lookup"><span data-stu-id="3cd77-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cd77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3cd77-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cd77-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3cd77-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="3cd77-106">no O identificador de instância do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="3cd77-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="3cd77-107">no Indica por que a função de ponto de entrada de DLL está sendo chamada.</span><span class="sxs-lookup"><span data-stu-id="3cd77-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="3cd77-108">Esse parâmetro pode ser um dos seguintes valores: DLL \_ PROCESS_ATTACH, dll de \_ thread \_ Attach, dll \_ \_ de anexação de thread \_ ou \_ reanexação de processo de dll.</span><span class="sxs-lookup"><span data-stu-id="3cd77-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="3cd77-109">Para obter descrições desses valores, consulte a `DllMain` documentação no Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="3cd77-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="3cd77-110">no Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="3cd77-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cd77-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3cd77-111">Return Value</span></span>  
 <span data-ttu-id="3cd77-112">Esse método retorna `true` para êxito e `false` se ocorre um erro.</span><span class="sxs-lookup"><span data-stu-id="3cd77-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cd77-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3cd77-113">Remarks</span></span>  
 <span data-ttu-id="3cd77-114">Essa função é chamada pelo carregador do sistema operacional para assemblies DLL.</span><span class="sxs-lookup"><span data-stu-id="3cd77-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="3cd77-115">Para assemblies executáveis, o carregador chama a função [ \_ CorExeMain](corexemain-function.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="3cd77-115">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="3cd77-116">O carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo DLL.</span><span class="sxs-lookup"><span data-stu-id="3cd77-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="3cd77-117">A `_CorDllMain` função é chamada diretamente pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="3cd77-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="3cd77-118">Para obter informações adicionais, consulte a seção comentários no tópico [ \_ CorValidateImage](corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3cd77-118">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cd77-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3cd77-119">Requirements</span></span>  

 <span data-ttu-id="3cd77-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cd77-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cd77-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3cd77-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3cd77-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3cd77-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3cd77-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cd77-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd77-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="3cd77-124">See also</span></span>

- [<span data-ttu-id="3cd77-125">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="3cd77-125">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
