---
title: Função GetALinkMessageDll
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787461"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="f7211-102">Função GetALinkMessageDll</span><span class="sxs-lookup"><span data-stu-id="f7211-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="f7211-103">Localiza e carrega a DLL de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f7211-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="f7211-104">Retornará 0 se a DLL de mensagem não puder ser localizada ou carregada.</span><span class="sxs-lookup"><span data-stu-id="f7211-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="f7211-105">A DLL de mensagem deve estar em um subdiretório cujo nome é uma ID de idioma ou no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="f7211-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7211-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7211-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f7211-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7211-107">Requirements</span></span>  
 <span data-ttu-id="f7211-108">**Cabeçalho:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="f7211-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="f7211-109">**Biblioteca**: Alink. dll</span><span class="sxs-lookup"><span data-stu-id="f7211-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7211-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7211-110">See also</span></span>

- [<span data-ttu-id="f7211-111">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="f7211-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
