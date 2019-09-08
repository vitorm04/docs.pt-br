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
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787622"
---
# <a name="createalink-function"></a><span data-ttu-id="0b8b5-102">Função CreateALink</span><span class="sxs-lookup"><span data-stu-id="0b8b5-102">CreateALink Function</span></span>
<span data-ttu-id="0b8b5-103">Cria uma instância do vinculador de assembly e define um ponteiro para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="0b8b5-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b8b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b8b5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b8b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b8b5-105">Parameters</span></span>  
  
|<span data-ttu-id="0b8b5-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="0b8b5-106">Parameter</span></span>|<span data-ttu-id="0b8b5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b8b5-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="0b8b5-108">O nome físico de uma das interfaces do vinculador de assembly.</span><span class="sxs-lookup"><span data-stu-id="0b8b5-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="0b8b5-109">O local em que a conclusão bem-sucedida contém um ponteiro para `riid` a interface.</span><span class="sxs-lookup"><span data-stu-id="0b8b5-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b8b5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b8b5-110">Requirements</span></span>  
 <span data-ttu-id="0b8b5-111">**Biblioteca**: Alink. dll</span><span class="sxs-lookup"><span data-stu-id="0b8b5-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8b5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b8b5-112">See also</span></span>

- [<span data-ttu-id="0b8b5-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="0b8b5-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
