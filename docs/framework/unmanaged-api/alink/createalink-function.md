---
title: Função CreateALink
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
ms.openlocfilehash: 9165a4db7e65fb0f409a902b06d32e9c2988aa69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446545"
---
# <a name="createalink-function"></a><span data-ttu-id="b1021-102">Função CreateALink</span><span class="sxs-lookup"><span data-stu-id="b1021-102">CreateALink Function</span></span>
<span data-ttu-id="b1021-103">Cria uma instância do vinculador de assembly e define um ponteiro para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="b1021-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1021-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1021-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1021-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1021-105">Parameters</span></span>  
  
|<span data-ttu-id="b1021-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="b1021-106">Parameter</span></span>|<span data-ttu-id="b1021-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1021-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="b1021-108">O nome físico de uma das interfaces do vinculador de assembly.</span><span class="sxs-lookup"><span data-stu-id="b1021-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="b1021-109">O local em que a conclusão bem-sucedida contém um ponteiro para a interface `riid`.</span><span class="sxs-lookup"><span data-stu-id="b1021-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1021-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b1021-110">Requirements</span></span>  
 <span data-ttu-id="b1021-111">**Biblioteca**: Alink. dll</span><span class="sxs-lookup"><span data-stu-id="b1021-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1021-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1021-112">See also</span></span>

- [<span data-ttu-id="b1021-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="b1021-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
