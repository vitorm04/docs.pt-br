---
title: Método ICorPublish::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 70255a89cee13abfe63b01351f8ffba51e54665a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396398"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="a2a97-102">Método ICorPublish::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="a2a97-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="a2a97-103">Obtém um enumerador para os processos gerenciados em execução neste computador.</span><span class="sxs-lookup"><span data-stu-id="a2a97-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2a97-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2a97-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2a97-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="a2a97-106">Um valor da enumeração de [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) que especifica o tipo de processo a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="a2a97-106">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="a2a97-107">Na versão atual, somente COR_PUB_MANAGEDONLY é válida.</span><span class="sxs-lookup"><span data-stu-id="a2a97-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="a2a97-108">Um ponteiro para o endereço de uma instância de [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) que é o enumerador dos processos.</span><span class="sxs-lookup"><span data-stu-id="a2a97-108">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2a97-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2a97-109">Remarks</span></span>  
 <span data-ttu-id="a2a97-110">A coleção de processos do enumerador é baseada em um instantâneo dos processos que estão em execução quando o `EnumProcesses` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="a2a97-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="a2a97-111">O enumerador não incluirá nenhum processo encerrado antes ou iniciado depois de `EnumProcesses` ser chamado.</span><span class="sxs-lookup"><span data-stu-id="a2a97-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="a2a97-112">O `EnumProcesses` método pode ser chamado mais de uma vez nessa instância de [ICorPublish](icorpublish-interface.md) para criar uma nova coleção atualizada de processos.</span><span class="sxs-lookup"><span data-stu-id="a2a97-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="a2a97-113">As coleções existentes não serão afetadas pelas chamadas subsequentes do `EnumProcesses` método.</span><span class="sxs-lookup"><span data-stu-id="a2a97-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2a97-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2a97-114">Requirements</span></span>  
 <span data-ttu-id="a2a97-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2a97-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2a97-116">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a2a97-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a2a97-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2a97-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2a97-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2a97-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a97-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="a2a97-119">See also</span></span>

- [<span data-ttu-id="a2a97-120">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="a2a97-120">ICorPublish Interface</span></span>](icorpublish-interface.md)
