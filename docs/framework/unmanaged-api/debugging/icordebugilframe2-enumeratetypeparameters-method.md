---
title: Método ICorDebugILFrame2::EnumerateTypeParameters
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a0c23c066a6f704c4dfcfbe254e91ab3bc5817e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416235"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="8c23d-102">Método ICorDebugILFrame2::EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="8c23d-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="8c23d-103">Obtém um objeto ICorDebugTypeEnum que contém o <xref:System.Type> parâmetros nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="8c23d-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c23d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c23d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c23d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c23d-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="8c23d-106">Um ponteiro para o endereço de um objeto de interface ICorDebugTypeEnum que permite a enumeração de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="8c23d-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="8c23d-107">A lista de parâmetros de tipo inclui os classe parâmetros de tipo (se houver) seguidos pelos parâmetros de tipo de método (se houver).</span><span class="sxs-lookup"><span data-stu-id="8c23d-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c23d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c23d-108">Remarks</span></span>  
 <span data-ttu-id="8c23d-109">Use o [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) método para determinar o número de parâmetros de tipo de classe e método de tipo contém esta lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8c23d-109">Use the [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="8c23d-110">Os parâmetros de tipo não estão sempre disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8c23d-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c23d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c23d-111">Requirements</span></span>  
 <span data-ttu-id="8c23d-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c23d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c23d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c23d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c23d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c23d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c23d-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c23d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
