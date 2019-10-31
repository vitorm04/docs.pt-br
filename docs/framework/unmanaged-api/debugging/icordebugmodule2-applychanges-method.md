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
ms.openlocfilehash: c324019e1e62701f4f2aaba1c00948b292ba6847
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127906"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="5c588-102">Método ICorDebugModule2::ApplyChanges</span><span class="sxs-lookup"><span data-stu-id="5c588-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="5c588-103">Aplica as alterações nos metadados e as alterações no código MSIL (Microsoft Intermediate Language) para o processo em execução.</span><span class="sxs-lookup"><span data-stu-id="5c588-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c588-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c588-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c588-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c588-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="5c588-106">no Tamanho, em bytes, dos metadados delta.</span><span class="sxs-lookup"><span data-stu-id="5c588-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="5c588-107">no Buffer que contém os metadados delta.</span><span class="sxs-lookup"><span data-stu-id="5c588-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="5c588-108">O endereço do buffer é retornado do método [IMetaDataEmit2:: SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5c588-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="5c588-109">Os endereços virtuais relativos (RVAs) nos metadados devem ser relativos ao início do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="5c588-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="5c588-110">no Tamanho, em bytes, do código MSIL do Delta.</span><span class="sxs-lookup"><span data-stu-id="5c588-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="5c588-111">no Buffer que contém o código MSIL atualizado.</span><span class="sxs-lookup"><span data-stu-id="5c588-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c588-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c588-112">Remarks</span></span>  
 <span data-ttu-id="5c588-113">O parâmetro `pbMetadata` está em um formato de metadados delta especial (como a saída de [IMetaDataEmit2:: SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="5c588-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="5c588-114">`pbMetadata` usa os metadados anteriores como base e descreve as alterações individuais a serem aplicadas a essa base.</span><span class="sxs-lookup"><span data-stu-id="5c588-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="5c588-115">Por outro lado, o parâmetro `pbIL[`] contém o novo MSIL para o método atualizado e é destinado a substituir completamente o MSIL anterior para esse método</span><span class="sxs-lookup"><span data-stu-id="5c588-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="5c588-116">Quando o MSIL do Delta e os metadados tiverem sido criados na memória do depurador, o depurador chamará `ApplyChanges` para enviar as alterações para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5c588-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="5c588-117">O tempo de execução atualiza suas tabelas de metadados, coloca o novo MSIL no processo e configura uma compilação JIT (just-in-time) do novo MSIL.</span><span class="sxs-lookup"><span data-stu-id="5c588-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="5c588-118">Quando as alterações tiverem sido aplicadas, o depurador deverá chamar [IMetaDataEmit2:: ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) para se preparar para a próxima sessão de edição.</span><span class="sxs-lookup"><span data-stu-id="5c588-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="5c588-119">O depurador pode continuar o processo.</span><span class="sxs-lookup"><span data-stu-id="5c588-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="5c588-120">Sempre que o depurador chama `ApplyChanges` em um módulo que tem metadados delta, ele também deve chamar [IMetaDataEmit:: ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) com os mesmos metadados delta em todas as suas cópias dos metadados desse módulo, exceto para a cópia usada para emitir as alterações.</span><span class="sxs-lookup"><span data-stu-id="5c588-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="5c588-121">Se uma cópia dos metadados de alguma forma estiver fora de sincronia com os metadados reais, o depurador sempre poderá acabar com a cópia e obter uma nova cópia.</span><span class="sxs-lookup"><span data-stu-id="5c588-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="5c588-122">Se o método de `ApplyChanges` falhar, a sessão de depuração estará em um estado inválido e deverá ser reiniciada.</span><span class="sxs-lookup"><span data-stu-id="5c588-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c588-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c588-123">Requirements</span></span>  
 <span data-ttu-id="5c588-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c588-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c588-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c588-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c588-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c588-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c588-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c588-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
