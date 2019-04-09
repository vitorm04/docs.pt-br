---
title: Enumeração WriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62e4328b75a7f6fecc28cd620ec3ac18460316c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111131"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="50bc8-102">Enumeração WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="50bc8-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="50bc8-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="50bc8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="50bc8-104">Fornece valores que especificam se as atualizações na memória para metadados estão visíveis para um depurador.</span><span class="sxs-lookup"><span data-stu-id="50bc8-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50bc8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50bc8-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="50bc8-106">Membros</span><span class="sxs-lookup"><span data-stu-id="50bc8-106">Members</span></span>  
  
|<span data-ttu-id="50bc8-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="50bc8-107">Member name</span></span>|<span data-ttu-id="50bc8-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="50bc8-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="50bc8-109">Manter a compatibilidade com versões anteriores do .NET Framework ao fazer atualizações na memória para metadados visíveis.</span><span class="sxs-lookup"><span data-stu-id="50bc8-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="50bc8-110">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="50bc8-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="50bc8-111">Fazer atualizações na memória para metadados visíveis para o depurador.</span><span class="sxs-lookup"><span data-stu-id="50bc8-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50bc8-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="50bc8-112">Remarks</span></span>  
 <span data-ttu-id="50bc8-113">Um membro do `WriteableMetadataUpdateMode` enumeração pode ser passada para o [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) método para controlar se as atualizações de na memória para metadados no processo de destino são visíveis para o depurador.</span><span class="sxs-lookup"><span data-stu-id="50bc8-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="50bc8-114">O `LegacyCompatPolicy` opção aplica o mesmo comportamento de versões do .NET Framework antes de 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="50bc8-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="50bc8-115">Geralmente, isso significa que os metadados de atualizações não estiver visível.</span><span class="sxs-lookup"><span data-stu-id="50bc8-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="50bc8-116">No entanto, chamadas para um número de métodos de depuração implicitamente forçar o depurador para fazer atualizações visíveis.</span><span class="sxs-lookup"><span data-stu-id="50bc8-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="50bc8-117">Por exemplo, se o depurador passa [icordebugilframe:: Getlocalvariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) o índice de uma variável não encontrado nos metadados de original do método, todos os metadados para o módulo é atualizado para um instantâneo de correspondência o estado atual das processo.</span><span class="sxs-lookup"><span data-stu-id="50bc8-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="50bc8-118">Em outras palavras, com o `LegacyCompatPolicy` opção, o depurador poderá ver nenhum, algumas ou todas as atualizações de metadados disponíveis, dependendo de como usar outras partes da API de depuração não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="50bc8-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50bc8-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50bc8-119">Requirements</span></span>  
 <span data-ttu-id="50bc8-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50bc8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50bc8-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50bc8-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50bc8-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50bc8-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="50bc8-123">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="50bc8-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50bc8-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50bc8-124">See also</span></span>

- [<span data-ttu-id="50bc8-125">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="50bc8-125">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="50bc8-126">Método SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="50bc8-126">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
