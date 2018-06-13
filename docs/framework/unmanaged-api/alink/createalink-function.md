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
ms.openlocfilehash: 1e29c9c246649229900beba2fcc9ab482071ae46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400660"
---
# <a name="createalink-function"></a><span data-ttu-id="5744e-102">Função CreateALink</span><span class="sxs-lookup"><span data-stu-id="5744e-102">CreateALink Function</span></span>
<span data-ttu-id="5744e-103">Cria uma instância de Assembly Linker e define um ponteiro para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="5744e-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5744e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5744e-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5744e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5744e-105">Parameters</span></span>  
  
|<span data-ttu-id="5744e-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="5744e-106">Parameter</span></span>|<span data-ttu-id="5744e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5744e-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="5744e-108">O nome físico de um Assembly Linker interfaces.</span><span class="sxs-lookup"><span data-stu-id="5744e-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="5744e-109">O local que contém um ponteiro para após a conclusão bem-sucedida de `riid` interface.</span><span class="sxs-lookup"><span data-stu-id="5744e-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5744e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5744e-110">Requirements</span></span>  
 <span data-ttu-id="5744e-111">**Biblioteca**: arquivo</span><span class="sxs-lookup"><span data-stu-id="5744e-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5744e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5744e-112">See Also</span></span>  
 [<span data-ttu-id="5744e-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="5744e-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
