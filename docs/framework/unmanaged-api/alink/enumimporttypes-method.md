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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d0aefea7345bc3bf37bdb8d13cb2cda19cfe527
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789944"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="faac9-102">Método EnumImportTypes</span><span class="sxs-lookup"><span data-stu-id="faac9-102">EnumImportTypes Method</span></span>

<span data-ttu-id="faac9-103">Enumera cada tipo em cada escopo.</span><span class="sxs-lookup"><span data-stu-id="faac9-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="faac9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="faac9-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="faac9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="faac9-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="faac9-106">Identificador para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="faac9-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="faac9-107">Número máximo de tipos para recuperar.</span><span class="sxs-lookup"><span data-stu-id="faac9-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="faac9-108">Recebe tokens do tipo, não deve exceder `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="faac9-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="faac9-109">Recebe o número real de tipo no `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="faac9-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="faac9-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="faac9-110">Return Value</span></span>

<span data-ttu-id="faac9-111">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="faac9-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="faac9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="faac9-112">Requirements</span></span>

<span data-ttu-id="faac9-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="faac9-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="faac9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faac9-114">See also</span></span>

- [<span data-ttu-id="faac9-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="faac9-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="faac9-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="faac9-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="faac9-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="faac9-117">ALink API</span></span>](index.md)