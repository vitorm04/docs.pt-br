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
ms.openlocfilehash: 0e480db953131d7771e493a8f367154a7d17dada
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396636"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="8b5cb-102">Interface ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="8b5cb-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="8b5cb-103">Estende a interface ICorDebugType para recuperar o identificador de tipo de um tipo base ou tipo complexo (definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="8b5cb-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b5cb-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8b5cb-104">Methods</span></span>  
  
|<span data-ttu-id="8b5cb-105">Método</span><span class="sxs-lookup"><span data-stu-id="8b5cb-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="8b5cb-106">Método GetTypeID</span><span class="sxs-lookup"><span data-stu-id="8b5cb-106">GetTypeID Method</span></span>](icordebugtype2-gettypeid-method.md)|<span data-ttu-id="8b5cb-107">Obtém um [COR_TYPEID](cor-typeid-structure.md) para este tipo.</span><span class="sxs-lookup"><span data-stu-id="8b5cb-107">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b5cb-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b5cb-108">Remarks</span></span>  
 <span data-ttu-id="8b5cb-109">Essa interface é uma extensão lógica da interface ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="8b5cb-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b5cb-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="8b5cb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b5cb-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b5cb-111">Example</span></span>  
 <span data-ttu-id="8b5cb-112">O fragmento de código a seguir ilustra o uso do método [ICorDebugType2:: GetTypeId](icordebugtype2-gettypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8b5cb-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="8b5cb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b5cb-113">Requirements</span></span>  
 <span data-ttu-id="8b5cb-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5cb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5cb-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b5cb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b5cb-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b5cb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b5cb-117">**.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b5cb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5cb-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="8b5cb-118">See also</span></span>

- [<span data-ttu-id="8b5cb-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8b5cb-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
