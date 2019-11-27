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
ms.openlocfilehash: a7ec50c91ce02958d0d44643d4f79da1680532aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450362"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="08a73-102">Método ICorProfilerInfo::GetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="08a73-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="08a73-103">Obtém um ponteiro para o corpo de um método no código da MSIL (Microsoft Intermediate Language), começando em seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="08a73-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a73-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08a73-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08a73-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08a73-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="08a73-106">no A ID do módulo no qual a função reside.</span><span class="sxs-lookup"><span data-stu-id="08a73-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="08a73-107">no O token de metadados para o método.</span><span class="sxs-lookup"><span data-stu-id="08a73-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="08a73-108">fora Um ponteiro para o cabeçalho do método.</span><span class="sxs-lookup"><span data-stu-id="08a73-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="08a73-109">fora Um inteiro que especifica o tamanho do método.</span><span class="sxs-lookup"><span data-stu-id="08a73-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08a73-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="08a73-110">Remarks</span></span>  
 <span data-ttu-id="08a73-111">Um método tem o escopo definido pelo módulo no qual reside.</span><span class="sxs-lookup"><span data-stu-id="08a73-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="08a73-112">Como o método `GetILFunctionBody` foi projetado para fornecer uma ferramenta de acesso ao código MSIL antes de ser carregado pelo Common Language Runtime (CLR), ele usa o token de metadados do método para localizar a instância desejada.</span><span class="sxs-lookup"><span data-stu-id="08a73-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="08a73-113">`GetILFunctionBody` pode retornar um CORPROF_E_FUNCTION_NOT_IL HRESULT se o `methodId` aponta para um método sem qualquer código MSIL (como um método abstrato ou um método de invocação de plataforma (PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="08a73-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08a73-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="08a73-114">Requirements</span></span>  
 <span data-ttu-id="08a73-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08a73-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08a73-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="08a73-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08a73-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08a73-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08a73-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08a73-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a73-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08a73-119">See also</span></span>

- [<span data-ttu-id="08a73-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="08a73-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
