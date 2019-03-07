---
title: Método ICorProfilerInfo::GetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e98ee26da2d78278435d90d6d04ef9771f41104
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489443"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="7a447-102">Método ICorProfilerInfo::GetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="7a447-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="7a447-103">Obtém um ponteiro para o corpo de um método no código do Microsoft intermediate language (MSIL), começando em seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="7a447-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a447-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a447-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a447-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a447-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="7a447-106">[in] A ID do módulo no qual a função reside.</span><span class="sxs-lookup"><span data-stu-id="7a447-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="7a447-107">[in] O token de metadados para o método.</span><span class="sxs-lookup"><span data-stu-id="7a447-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="7a447-108">[out] Um ponteiro para o cabeçalho do método.</span><span class="sxs-lookup"><span data-stu-id="7a447-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="7a447-109">[out] Um inteiro que especifica o tamanho do método.</span><span class="sxs-lookup"><span data-stu-id="7a447-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a447-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a447-110">Remarks</span></span>  
 <span data-ttu-id="7a447-111">Um método é delimitado pelo módulo no qual ele reside.</span><span class="sxs-lookup"><span data-stu-id="7a447-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="7a447-112">Porque o `GetILFunctionBody` método foi projetado para fornecer um acesso à ferramenta para o código MSIL antes de eles terem sido carregados pelo common language runtime (CLR), ele usa o token de metadados do método para localizar a instância desejada.</span><span class="sxs-lookup"><span data-stu-id="7a447-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="7a447-113">`GetILFunctionBody` pode retornar um HRESULT de CORPROF_E_FUNCTION_NOT_IL se o `methodId` aponta para um método sem qualquer MSIL de código (como um método abstrato ou uma plataforma de invocação de método (PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="7a447-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a447-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a447-114">Requirements</span></span>  
 <span data-ttu-id="7a447-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a447-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a447-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a447-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a447-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a447-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a447-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a447-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a447-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a447-119">See also</span></span>
- [<span data-ttu-id="7a447-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7a447-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
