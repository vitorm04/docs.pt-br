---
title: "Método ICorDebugType::GetBase"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de00e519b43d486e70d5ed8165eed01b59d6e725
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="e75d2-102">Método ICorDebugType::GetBase</span><span class="sxs-lookup"><span data-stu-id="e75d2-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="e75d2-103">Obtém um ponteiro de interface para um ICorDebugType que representa o tipo base, se houver, do tipo representado por esse `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e75d2-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e75d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e75d2-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e75d2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e75d2-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="e75d2-106">[out] Um ponteiro para o endereço de uma `ICorDebugType` objeto que representa o tipo base.</span><span class="sxs-lookup"><span data-stu-id="e75d2-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e75d2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e75d2-107">Remarks</span></span>  
 <span data-ttu-id="e75d2-108">Pesquisar o tipo base para um tipo é útil para implementar a funcionalidade comum do depurador, como na impressão de todos os campos de um objeto ou suas classes pai.</span><span class="sxs-lookup"><span data-stu-id="e75d2-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e75d2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e75d2-109">Requirements</span></span>  
 <span data-ttu-id="e75d2-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e75d2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e75d2-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e75d2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e75d2-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e75d2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e75d2-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e75d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
