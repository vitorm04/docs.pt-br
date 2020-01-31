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
ms.openlocfilehash: 5c3f2f7a9c0804b71c9c8a52bb032aca7c03825e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790300"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="ec707-102">Enumeração WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="ec707-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="ec707-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="ec707-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ec707-104">Fornece valores que especificam se as atualizações na memória para metadados estão visíveis para um depurador.</span><span class="sxs-lookup"><span data-stu-id="ec707-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec707-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec707-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="ec707-106">Membros</span><span class="sxs-lookup"><span data-stu-id="ec707-106">Members</span></span>  
  
|<span data-ttu-id="ec707-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="ec707-107">Member name</span></span>|<span data-ttu-id="ec707-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec707-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="ec707-109">Mantenha a compatibilidade com as versões anteriores do .NET Framework ao fazer atualizações na memória para os metadados visíveis.</span><span class="sxs-lookup"><span data-stu-id="ec707-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="ec707-110">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ec707-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="ec707-111">Faça atualizações na memória para os metadados visíveis para o depurador.</span><span class="sxs-lookup"><span data-stu-id="ec707-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec707-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec707-112">Remarks</span></span>  
 <span data-ttu-id="ec707-113">Um membro da enumeração `WriteableMetadataUpdateMode` pode ser passado para o método [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) para controlar se as atualizações na memória para os metadados no processo de destino são visíveis para o depurador.</span><span class="sxs-lookup"><span data-stu-id="ec707-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="ec707-114">A opção `LegacyCompatPolicy` impõe o mesmo comportamento das versões do .NET Framework antes de 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="ec707-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="ec707-115">Isso geralmente significa que os metadados de atualizações não são visíveis.</span><span class="sxs-lookup"><span data-stu-id="ec707-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="ec707-116">No entanto, as chamadas para vários métodos de depuração convertem implicitamente o depurador para tornar as atualizações visíveis.</span><span class="sxs-lookup"><span data-stu-id="ec707-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="ec707-117">Por exemplo, se o depurador passar [ICorDebugILFrame:: GetLocalVariable](icordebugilframe-getlocalvariable-method.md) o índice de uma variável não for encontrado nos metadados originais do método, todos os metadados do módulo serão atualizados para um instantâneo que corresponde ao estado atual do processo.</span><span class="sxs-lookup"><span data-stu-id="ec707-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="ec707-118">Em outras palavras, com a opção `LegacyCompatPolicy`, o depurador pode ver nenhuma, algumas ou todas as atualizações de metadados disponíveis, dependendo de como ela usa outras partes da API de depuração não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="ec707-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec707-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ec707-119">Requirements</span></span>  
 <span data-ttu-id="ec707-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec707-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec707-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec707-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec707-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec707-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec707-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec707-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec707-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="ec707-124">See also</span></span>

- [<span data-ttu-id="ec707-125">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="ec707-125">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="ec707-126">Método SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="ec707-126">SetWriteableMetadataUpdateMode Method</span></span>](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
