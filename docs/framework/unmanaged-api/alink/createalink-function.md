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
ms.openlocfilehash: 993848711f41c9e03b969a3c611982a5c8bc860d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742212"
---
# <a name="createalink-function"></a><span data-ttu-id="fb7e4-102">Função CreateALink</span><span class="sxs-lookup"><span data-stu-id="fb7e4-102">CreateALink Function</span></span>
<span data-ttu-id="fb7e4-103">Cria uma instância do vinculador de Assembly e define um ponteiro para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb7e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb7e4-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb7e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb7e4-105">Parameters</span></span>  
  
|<span data-ttu-id="fb7e4-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="fb7e4-106">Parameter</span></span>|<span data-ttu-id="fb7e4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb7e4-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="fb7e4-108">O nome físico de uma das interfaces de vinculador de Assembly.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="fb7e4-109">O local que contém um ponteiro para a conclusão bem-sucedida de `riid` interface.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb7e4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb7e4-110">Requirements</span></span>  
 <span data-ttu-id="fb7e4-111">**Biblioteca**: ALink</span><span class="sxs-lookup"><span data-stu-id="fb7e4-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb7e4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb7e4-112">See also</span></span>

- [<span data-ttu-id="fb7e4-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="fb7e4-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
