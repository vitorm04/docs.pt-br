---
title: Método ICorDebugModule2::ApplyChanges
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a406e945a67352bc7f126b40bd56f4a11dd693b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="58ef6-102">Método ICorDebugModule2::ApplyChanges</span><span class="sxs-lookup"><span data-stu-id="58ef6-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="58ef6-103">Aplica as alterações nos metadados e as alterações no código Microsoft intermediate language (MSIL) para o processo em execução.</span><span class="sxs-lookup"><span data-stu-id="58ef6-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ef6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58ef6-104">Syntax</span></span>  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58ef6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58ef6-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="58ef6-106">[in] Tamanho, em bytes, dos metadados do delta.</span><span class="sxs-lookup"><span data-stu-id="58ef6-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="58ef6-107">[in] Buffer que contém os metadados de delta.</span><span class="sxs-lookup"><span data-stu-id="58ef6-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="58ef6-108">O endereço do buffer é retornado do [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="58ef6-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="58ef6-109">Os endereços virtuais relativos (RVAs) nos metadados devem ser relativo ao início do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="58ef6-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="58ef6-110">[in] Tamanho, em bytes, de delta código MSIL.</span><span class="sxs-lookup"><span data-stu-id="58ef6-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="58ef6-111">[in] Buffer que contém o código MSIL atualizado.</span><span class="sxs-lookup"><span data-stu-id="58ef6-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58ef6-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="58ef6-112">Remarks</span></span>  
 <span data-ttu-id="58ef6-113">O `pbMetadata` parâmetro está em um formato de metadados de delta especiais (como saída pelo [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="58ef6-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="58ef6-114">`pbMetadata` usa metadados anterior como base e descreve as alterações individuais para aplicar a essa base.</span><span class="sxs-lookup"><span data-stu-id="58ef6-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="58ef6-115">Em contraste, o `pbIL[`] parâmetro contém o MSIL novo para o método de atualização e é usado para substituir completamente o MSIL anterior para o método</span><span class="sxs-lookup"><span data-stu-id="58ef6-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="58ef6-116">Quando o delta MSIL e os metadados foram criadas na memória do depurador, o depurador chama `ApplyChanges` para enviar as alterações para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="58ef6-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="58ef6-117">O tempo de execução suas tabelas de metadados de atualizações, coloca o novo MSIL no processo e configura uma just-in-time compilação JIT () do novo MSIL.</span><span class="sxs-lookup"><span data-stu-id="58ef6-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="58ef6-118">Quando as alterações tiverem sido aplicadas, o depurador deve chamar [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) para se preparar para a próxima sessão de edição.</span><span class="sxs-lookup"><span data-stu-id="58ef6-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="58ef6-119">O depurador pode então continuar o processo.</span><span class="sxs-lookup"><span data-stu-id="58ef6-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="58ef6-120">Sempre que o depurador chama `ApplyChanges` em um módulo que tem metadados de delta, ele também deve chamar [: Applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) com os mesmos metadados delta em todas as cópias dos metadados do módulo, exceto a cópia usado para emitir as alterações.</span><span class="sxs-lookup"><span data-stu-id="58ef6-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="58ef6-121">Se uma cópia dos metadados de alguma forma ficar fora de sincronia com os metadados, o depurador sempre pode descartar essa cópia e obtenha uma nova cópia.</span><span class="sxs-lookup"><span data-stu-id="58ef6-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="58ef6-122">Se o `ApplyChanges` método falhar, a depuração sessão está em um estado inválido e deve ser reiniciada.</span><span class="sxs-lookup"><span data-stu-id="58ef6-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ef6-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58ef6-123">Requirements</span></span>  
 <span data-ttu-id="58ef6-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ef6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ef6-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58ef6-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58ef6-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58ef6-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58ef6-127">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ef6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
