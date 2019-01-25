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
ms.openlocfilehash: f809395de68b596f769f9396da8668bf296b1aa2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675035"
---
# <a name="createalink-function"></a><span data-ttu-id="9473c-102">Função CreateALink</span><span class="sxs-lookup"><span data-stu-id="9473c-102">CreateALink Function</span></span>
<span data-ttu-id="9473c-103">Cria uma instância do vinculador de Assembly e define um ponteiro para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="9473c-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9473c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9473c-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9473c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9473c-105">Parameters</span></span>  
  
|<span data-ttu-id="9473c-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9473c-106">Parameter</span></span>|<span data-ttu-id="9473c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9473c-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="9473c-108">O nome físico de uma das interfaces de vinculador de Assembly.</span><span class="sxs-lookup"><span data-stu-id="9473c-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="9473c-109">O local que contém um ponteiro para a conclusão bem-sucedida de `riid` interface.</span><span class="sxs-lookup"><span data-stu-id="9473c-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9473c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9473c-110">Requirements</span></span>  
 <span data-ttu-id="9473c-111">**Biblioteca**: ALink</span><span class="sxs-lookup"><span data-stu-id="9473c-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9473c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9473c-112">See also</span></span>
- [<span data-ttu-id="9473c-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="9473c-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
