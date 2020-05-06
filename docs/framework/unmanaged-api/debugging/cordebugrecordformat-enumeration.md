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
ms.openlocfilehash: cfbd856c73ab10642a7cf7c16cfb2d70e7fe9756
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795723"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="7f350-102">Enumeração CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="7f350-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="7f350-103">Descreve o formato dos dados em uma matriz de bytes que contém informações sobre um evento de depuração de exceção nativo.</span><span class="sxs-lookup"><span data-stu-id="7f350-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f350-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f350-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="7f350-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7f350-105">Members</span></span>  
  
|<span data-ttu-id="7f350-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7f350-106">Member</span></span>|<span data-ttu-id="7f350-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f350-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="7f350-108">Os dados serão um registro de exceção do Windows de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7f350-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="7f350-109">Os dados serão um registro de exceção do Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7f350-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f350-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f350-110">Remarks</span></span>  
 <span data-ttu-id="7f350-111">Um membro da `CorDebugRecordFormat` enumeração é passado para o método [DecodeEvent](icordebugprocess6-decodeevent-method.md) para indicar o formato da matriz de bytes em seu `pRecord` argumento.</span><span class="sxs-lookup"><span data-stu-id="7f350-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f350-112">Essa enumeração destina-se ao uso em cenários de depuração .NET Native apenas.</span><span class="sxs-lookup"><span data-stu-id="7f350-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f350-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f350-113">Requirements</span></span>  
 <span data-ttu-id="7f350-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f350-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f350-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f350-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f350-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f350-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f350-117">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f350-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f350-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f350-118">See also</span></span>

- [<span data-ttu-id="7f350-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="7f350-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
