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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11117db08d58684cc854400424d1836ec35b8c12
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497997"
---
# <a name="createalink-function"></a><span data-ttu-id="13c8e-102">Função CreateALink</span><span class="sxs-lookup"><span data-stu-id="13c8e-102">CreateALink Function</span></span>
<span data-ttu-id="13c8e-103">Cria uma instância do vinculador de Assembly e define um ponteiro para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="13c8e-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c8e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13c8e-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13c8e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13c8e-105">Parameters</span></span>  
  
|<span data-ttu-id="13c8e-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="13c8e-106">Parameter</span></span>|<span data-ttu-id="13c8e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="13c8e-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="13c8e-108">O nome físico de uma das interfaces de vinculador de Assembly.</span><span class="sxs-lookup"><span data-stu-id="13c8e-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="13c8e-109">O local que contém um ponteiro para a conclusão bem-sucedida de `riid` interface.</span><span class="sxs-lookup"><span data-stu-id="13c8e-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13c8e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13c8e-110">Requirements</span></span>  
 <span data-ttu-id="13c8e-111">**Biblioteca**: ALink</span><span class="sxs-lookup"><span data-stu-id="13c8e-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c8e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13c8e-112">See also</span></span>
- [<span data-ttu-id="13c8e-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="13c8e-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
