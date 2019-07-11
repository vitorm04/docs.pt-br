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
ms.openlocfilehash: 860b87b09ee487f893a1bba2aaa34292c50ffcb7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764347"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="3dcb9-102">Método ICorDebugModule2::ApplyChanges</span><span class="sxs-lookup"><span data-stu-id="3dcb9-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="3dcb9-103">Aplica as alterações nos metadados e as alterações no código Microsoft intermediate language (MSIL) para o processo em execução.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dcb9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3dcb9-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dcb9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3dcb9-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="3dcb9-106">[in] Tamanho, em bytes, dos metadados do delta.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="3dcb9-107">[in] Buffer que contém os metadados de delta.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="3dcb9-108">O endereço do buffer é retornado do [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="3dcb9-109">Os endereços virtuais (relacionados RVAs) nos metadados devem ser relativo ao início do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="3dcb9-110">[in] Tamanho, em bytes, do código MSIL delta.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="3dcb9-111">[in] Buffer que contém o código MSIL atualizado.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dcb9-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="3dcb9-112">Remarks</span></span>  
 <span data-ttu-id="3dcb9-113">O `pbMetadata` parâmetro está em um formato de metadados de delta especiais (como saída pelo [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="3dcb9-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="3dcb9-114">`pbMetadata` usa metadados anterior como base e descreve as alterações individuais se aplicam a essa base.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="3dcb9-115">Em contraste, o `pbIL[`] parâmetro contém o novo MSIL para o método atualizado e é usado para substituir completamente o MSIL para o método anterior</span><span class="sxs-lookup"><span data-stu-id="3dcb9-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="3dcb9-116">Quando o delta MSIL e os metadados foram criados na memória do depurador, o depurador chama `ApplyChanges` para enviar as alterações para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3dcb9-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="3dcb9-117">O tempo de execução atualiza suas tabelas de metadados, coloca o MSIL de novo no processo e configura uma compilação de (JIT) just-in-time do novo MSIL.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="3dcb9-118">Quando as alterações tiverem sido aplicadas, o depurador deve chamar [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) para se preparar para a próxima sessão de edição.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="3dcb9-119">O depurador pode, em seguida, continue o processo.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="3dcb9-120">Sempre que o depurador chama `ApplyChanges` em um módulo que tem metadados de delta, ele também deve chamar [imetadataemit:: Applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) com os mesmos metadados delta em todas as cópias dos metadados do módulo, exceto a cópia de usado para emitir as alterações.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="3dcb9-121">Se uma cópia dos metadados de alguma forma ficar fora de sincronia com os metadados reais, o depurador sempre pode jogar fora essa cópia e obter uma nova cópia.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="3dcb9-122">Se o `ApplyChanges` método falhar, a depuração sessão estiver em um estado inválido e deve ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dcb9-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3dcb9-123">Requirements</span></span>  
 <span data-ttu-id="3dcb9-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dcb9-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dcb9-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dcb9-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dcb9-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dcb9-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dcb9-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dcb9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
