---
title: "Função CreateALink"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateALink
api_location: alink.dll
api_type: DLLExport
f1_keywords: CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a><span data-ttu-id="7b170-102">Função CreateALink</span><span class="sxs-lookup"><span data-stu-id="7b170-102">CreateALink Function</span></span>
<span data-ttu-id="7b170-103">Cria uma instância de Assembly Linker e define um ponteiro para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="7b170-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b170-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b170-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b170-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b170-105">Parameters</span></span>  
  
|<span data-ttu-id="7b170-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="7b170-106">Parameter</span></span>|<span data-ttu-id="7b170-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b170-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="7b170-108">O nome físico de um Assembly Linker interfaces.</span><span class="sxs-lookup"><span data-stu-id="7b170-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="7b170-109">O local que contém um ponteiro para após a conclusão bem-sucedida de `riid` interface.</span><span class="sxs-lookup"><span data-stu-id="7b170-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b170-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b170-110">Requirements</span></span>  
 <span data-ttu-id="7b170-111">**Biblioteca**: arquivo</span><span class="sxs-lookup"><span data-stu-id="7b170-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b170-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b170-112">See Also</span></span>  
 [<span data-ttu-id="7b170-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="7b170-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
