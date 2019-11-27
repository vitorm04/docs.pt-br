---
title: Método EnumImportTypes
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448740"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="9126b-102">Método EnumImportTypes</span><span class="sxs-lookup"><span data-stu-id="9126b-102">EnumImportTypes Method</span></span>

<span data-ttu-id="9126b-103">Enumera cada tipo em cada escopo.</span><span class="sxs-lookup"><span data-stu-id="9126b-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="9126b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9126b-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="9126b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9126b-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="9126b-106">Identificador para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="9126b-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="9126b-107">Número máximo de tipos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="9126b-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="9126b-108">Recebe tokens de tipo, sem exceder `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="9126b-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="9126b-109">Recebe o número real do tipo em `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="9126b-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="9126b-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9126b-110">Return Value</span></span>

<span data-ttu-id="9126b-111">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="9126b-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="9126b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9126b-112">Requirements</span></span>

<span data-ttu-id="9126b-113">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="9126b-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="9126b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9126b-114">See also</span></span>

- [<span data-ttu-id="9126b-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9126b-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9126b-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9126b-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9126b-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9126b-117">ALink API</span></span>](index.md)
