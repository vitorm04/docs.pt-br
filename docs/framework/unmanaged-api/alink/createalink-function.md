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
ms.openlocfilehash: b494b8b776f4cb0eb534233c5a03ab2d34a698ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115616"
---
# <a name="createalink-function"></a><span data-ttu-id="20769-102">Função CreateALink</span><span class="sxs-lookup"><span data-stu-id="20769-102">CreateALink Function</span></span>
<span data-ttu-id="20769-103">Cria uma instância do vinculador de Assembly e define um ponteiro para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="20769-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20769-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20769-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20769-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20769-105">Parameters</span></span>  
  
|<span data-ttu-id="20769-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="20769-106">Parameter</span></span>|<span data-ttu-id="20769-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="20769-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="20769-108">O nome físico de uma das interfaces de vinculador de Assembly.</span><span class="sxs-lookup"><span data-stu-id="20769-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="20769-109">O local que contém um ponteiro para a conclusão bem-sucedida de `riid` interface.</span><span class="sxs-lookup"><span data-stu-id="20769-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20769-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20769-110">Requirements</span></span>  
 <span data-ttu-id="20769-111">**Biblioteca**: ALink</span><span class="sxs-lookup"><span data-stu-id="20769-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20769-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20769-112">See also</span></span>

- [<span data-ttu-id="20769-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="20769-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
