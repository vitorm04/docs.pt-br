---
title: Interface ICorDebugType2
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 878941f7af71fa5e3de8e38c4a68a66cb964983d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223154"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="a7257-102">Interface ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="a7257-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="a7257-103">Estende a interface ICorDebugType para recuperar o identificador de tipo de um tipo base ou um tipo complexo (definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="a7257-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7257-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a7257-104">Methods</span></span>  
  
|<span data-ttu-id="a7257-105">Método</span><span class="sxs-lookup"><span data-stu-id="a7257-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="a7257-106">Método GetTypeID</span><span class="sxs-lookup"><span data-stu-id="a7257-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="a7257-107">Obtém uma [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="a7257-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7257-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7257-108">Remarks</span></span>  
 <span data-ttu-id="a7257-109">Essa interface é uma extensão lógica da interface ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="a7257-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7257-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="a7257-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7257-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7257-111">Example</span></span>  
 <span data-ttu-id="a7257-112">O fragmento de código a seguir ilustra o uso do [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a7257-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="a7257-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7257-113">Requirements</span></span>  
 <span data-ttu-id="a7257-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7257-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7257-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7257-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7257-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7257-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a7257-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a7257-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a7257-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7257-118">See also</span></span>

- [<span data-ttu-id="a7257-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a7257-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
