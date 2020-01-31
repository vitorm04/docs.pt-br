---
title: ICorDebugILFrame4::Método EnumerateLocalVariablesEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: afeec3df03fc2b122ca8deb8123b79314b5e3837
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782430"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="b7132-102">ICorDebugILFrame4::Método EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="b7132-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="b7132-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="b7132-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b7132-104">Obtém um enumerador da variável local no quadro e, opcionalmente, inclui variáveis incluídas na instrumentação ReJIT do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="b7132-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7132-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7132-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7132-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7132-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="b7132-107">no Um membro de enumeração [ILCodeKind](ilcodekind-enumeration.md) que especifica se as variáveis adicionadas na instrumentação do profiler ReJIT estão incluídas no quadro.</span><span class="sxs-lookup"><span data-stu-id="b7132-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="b7132-108">fora Um ponteiro para o endereço de um objeto "ICorDebugValueEnum" que é o enumerador para as variáveis locais neste quadro.</span><span class="sxs-lookup"><span data-stu-id="b7132-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7132-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7132-109">Remarks</span></span>  
 <span data-ttu-id="b7132-110">Esse método é semelhante ao método [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) , exceto que ele, opcionalmente, acessa variáveis adicionadas na instrumentação do profiler ReJIT.</span><span class="sxs-lookup"><span data-stu-id="b7132-110">This method is similar to the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="b7132-111">A configuração de `flags` como `ILCODE_ORIGINAL_IL` é equivalente a chamar [ICorDebugILFrame:: EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="b7132-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="b7132-112">Configurar `flags` para `ILCODE_REJIT_IL` permite ao depurador acessar as variáveis locais incluídas na instrumentação ReJIT do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="b7132-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="b7132-113">Se a linguagem intermediária (IL) não estiver instrumentada, a enumeração estará vazia e o método retornará `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="b7132-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="b7132-114">O enumerador poderá não incluir todas as variáveis locais no método em execução, considerando que algumas delas podem não estar ativas.</span><span class="sxs-lookup"><span data-stu-id="b7132-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7132-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b7132-115">Requirements</span></span>  
 <span data-ttu-id="b7132-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7132-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7132-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7132-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7132-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7132-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7132-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7132-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7132-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="b7132-120">See also</span></span>

- [<span data-ttu-id="b7132-121">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="b7132-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="b7132-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b7132-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b7132-123">ReJIT: um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="b7132-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
