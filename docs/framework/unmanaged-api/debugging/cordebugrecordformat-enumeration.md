---
title: Enumeração CorDebugRecordFormat
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: add1458bb3a50a5e5433e8cc7baaf47d750c927d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645702"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="36a66-102">Enumeração CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="36a66-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="36a66-103">Descreve o formato dos dados em uma matriz de bytes que contém informações sobre um evento de depuração de exceção nativo.</span><span class="sxs-lookup"><span data-stu-id="36a66-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36a66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36a66-104">Syntax</span></span>  
  
```  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="36a66-105">Membros</span><span class="sxs-lookup"><span data-stu-id="36a66-105">Members</span></span>  
  
|<span data-ttu-id="36a66-106">Membro</span><span class="sxs-lookup"><span data-stu-id="36a66-106">Member</span></span>|<span data-ttu-id="36a66-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="36a66-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="36a66-108">Os dados serão um registro de exceção do Windows de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="36a66-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="36a66-109">Os dados serão um registro de exceção do Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="36a66-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36a66-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="36a66-110">Remarks</span></span>  
 <span data-ttu-id="36a66-111">Um membro do `CorDebugRecordFormat` enumeração é passada para o [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) método para indicar o formato da matriz de bytes no seu `pRecord` argumento.</span><span class="sxs-lookup"><span data-stu-id="36a66-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36a66-112">Essa enumeração destina-se para uso no .NET Native somente para cenários de depuração.</span><span class="sxs-lookup"><span data-stu-id="36a66-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36a66-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36a66-113">Requirements</span></span>  
 <span data-ttu-id="36a66-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36a66-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36a66-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36a66-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36a66-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36a66-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36a66-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36a66-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a66-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36a66-118">See also</span></span>

- [<span data-ttu-id="36a66-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="36a66-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
