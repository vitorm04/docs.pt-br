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
ms.openlocfilehash: 239b1a9f258f435e6dcca6e00cc20df5b5c01188
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097448"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="61fb2-102">Enumeração CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="61fb2-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="61fb2-103">Descreve o formato dos dados em uma matriz de bytes que contém informações sobre um evento de depuração de exceção nativo.</span><span class="sxs-lookup"><span data-stu-id="61fb2-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61fb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61fb2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="61fb2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="61fb2-105">Members</span></span>  
  
|<span data-ttu-id="61fb2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="61fb2-106">Member</span></span>|<span data-ttu-id="61fb2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="61fb2-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="61fb2-108">Os dados serão um registro de exceção do Windows de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="61fb2-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="61fb2-109">Os dados serão um registro de exceção do Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="61fb2-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61fb2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="61fb2-110">Remarks</span></span>  
 <span data-ttu-id="61fb2-111">Um membro da enumeração `CorDebugRecordFormat` é passado para o método [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) para indicar o formato da matriz de bytes em seu argumento `pRecord`.</span><span class="sxs-lookup"><span data-stu-id="61fb2-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61fb2-112">Essa enumeração destina-se ao uso em cenários de depuração .NET Native apenas.</span><span class="sxs-lookup"><span data-stu-id="61fb2-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61fb2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61fb2-113">Requirements</span></span>  
 <span data-ttu-id="61fb2-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61fb2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61fb2-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61fb2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61fb2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61fb2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61fb2-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61fb2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61fb2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61fb2-118">See also</span></span>

- [<span data-ttu-id="61fb2-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="61fb2-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
